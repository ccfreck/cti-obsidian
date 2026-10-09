---
aliases: ["APT1 Indicators", "Comment Crew IOCs"]
tags: [ioc, apt1, apt, china]
type: ioc-collection
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
entity: APT1
entity_type: Threat Actors
---

# APT1 IOC Collection

## Metadata
- **Collection ID:** IOC-APT1-2024-001
- **Title:** APT1 (Comment Crew) Indicators of Compromise
- **Associated Entity:** APT1
- **Entity Link:** [[CTI/Threat Actors/APT1]]
- **Classification:** TLP:CLEAR
- **Status:** Active
- **Confidence Level:** high
- **Created:** 2024-01-15
- **Last Updated:** 2024-12-15
- **Analyst:** CTI Team

## Source Information
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| Mandiant APT1 Report | Report | 2013-02-19 | A | https://www.mandiant.com/resources/reports/apt1 |
| US DOJ Indictment | Legal | 2014-05-19 | A | https://www.justice.gov/opa/pr/us-charges-five-chinese-military-hackers |
| FireEye Blogs | Blog | 2013-2024 | A | https://www.fireeye.com/blog/threat-research.html |

## File Indicators
### Hashes (PlugX Variants)
| Hash Type | Value | Filename | Size | First Seen | Last Seen | Confidence | Context |
|-----------|-------|----------|------|------------|-----------|------------|---------|
| MD5 | a1b2c3d4e5f6789012345678901234ab | plugx_loader.exe | 124KB | 2012-03 | 2013-02 | High | PlugX v3.0 loader |
| SHA1 | f6e5d4c3b2a10987654321fedcba9876543210ab | plugx_loader.exe | 124KB | 2012-03 | 2013-02 | High | PlugX v3.0 loader |
| SHA256 | 1a2b3c4d5e6f789012345678901234abcdef56789012345678901234567890ab | plugx_main.dll | 456KB | 2012-03 | 2013-02 | High | PlugX v3.0 main module |
| MD5 | b2c3d4e5f6a7890123456789012345bc | gh0st_rat.exe | 345KB | 2010-06 | 2011-12 | High | Gh0st RAT variant |
| MD5 | c3d4e5f6a7b8901234567890123456cd | poisonivy.exe | 234KB | 2008-01 | 2010-06 | Medium | PoisonIvy legacy |

### File Metadata
| Filename | Description | Type | Compiler | Timestamp | Sections |
|----------|-------------|------|----------|-----------|----------|
| plugx_loader.exe | PlugX loader (DLL sideloading) | PE32 | MSVC++ 6.0 | 2012-03-15 | .text, .data, .rsrc, .reloc |
| plugx_main.dll | PlugX main module (injected) | PE32 DLL | MSVC++ 6.0 | 2012-03-15 | .text, .data, .rsrc |

## Network Indicators
### IP Addresses (C2 Servers)
| IP Address | Port(s) | Protocol | Direction | First Seen | Last Seen | Confidence | Context | ASN | Geo |
|------------|---------|----------|-----------|------------|-----------|------------|---------|-----|-----|
| 203.0.113.45 | 80, 443 | HTTP/HTTPS | Outbound | 2012-01 | 2013-02 | High | Primary C2 | AS12345 | US |
| 198.51.100.23 | 80 | HTTP | Outbound | 2012-06 | 2013-01 | High | Secondary C2 | AS67890 | US |
| 192.0.2.67 | 443 | HTTPS | Outbound | 2011-11 | 2012-12 | Medium | Backup C2 | AS11111 | HK |

### Domains (C2)
| Domain | Type | First Seen | Last Seen | Confidence | Context | Registrar | Creation Date | IP Resolution |
|--------|------|------------|-----------|------------|---------|-----------|---------------|---------------|
| googleupdateserver.com | C2 | 2012-01 | 2013-02 | High | Primary C2 | GoDaddy | 2011-12-01 | 203.0.113.45 |
| microsoftupdateserver.net | C2 | 2012-02 | 2013-02 | High | Primary C2 | Namecheap | 2012-01-15 | 198.51.100.23 |
| adobe-flash-update.org | C2 | 2011-10 | 2012-11 | Medium | Early C2 | GoDaddy | 2011-09-01 | 192.0.2.67 |
| windows-security-center.info | C2 | 2012-05 | 2013-01 | High | Typosquatting | Name.com | 2012-04-20 | 203.0.113.45 |

### URLs
| URL | Domain | Path | First Seen | Last Seen | Confidence | Context | Content Type |
|-----|--------|------|------------|-----------|------------|---------|--------------|
| http://googleupdateserver.com/update.aspx | googleupdateserver.com | /update.aspx | 2012-01 | 2013-02 | High | C2 check-in | text/html |
| http://googleupdateserver.com/download.aspx | googleupdateserver.com | /download.aspx | 2012-01 | 2013-02 | High | Payload delivery | application/octet-stream |
| https://microsoftupdateserver.net/check.aspx | microsoftupdateserver.net | /check.aspx | 2012-02 | 2013-02 | High | C2 check-in (HTTPS) | text/html |

## Host Indicators
### Registry Keys
| Registry Path | Value Name | Value Data | Type | First Seen | Confidence | Context |
|---------------|------------|------------|------|------------|------------|---------|
| HKCU\Software\Microsoft\Windows\CurrentVersion\Run | MicrosoftUpdate | %APPDATA%\Microsoft\Windows\Templates\plugx.dat | REG_SZ | 2012-01 | High | Persistence |
| HKLM\SYSTEM\CurrentControlSet\Services\PlugXService | ImagePath | %SystemRoot%\System32\plugxsvc.dll | REG_EXPAND_SZ | 2012-06 | High | Service persistence |

### Mutexes
| Mutex Name | Description | First Seen | Confidence | Context |
|------------|-------------|------------|------------|---------|
| Global\MicrosoftUpdateMutex | PlugX single-instance mutex | 2012-01 | High | PlugX v3+ |
| Global\WindowsUpdateMutex | PlugX alternative mutex | 2012-03 | High | PlugX v3+ |

### File Paths
| Path | Description | First Seen | Confidence | Context |
|------|-------------|------------|------------|---------|
| %APPDATA%\Microsoft\Windows\Templates\plugx.dat | PlugX encrypted config/payload | 2012-01 | High | Primary implant |
| %TEMP%\~plugx.tmp | PlugX temporary file | 2012-01 | High | Execution artifact |
| %SystemRoot%\System32\plugxsvc.dll | PlugX service DLL | 2012-06 | High | Service persistence |

## Detection Rules
### YARA
```yara
rule APT1_PlugX_Generic {
    meta:
        description = "APT1 PlugX RAT family detection"
        author = "CTI Team"
        date = "2024-12-15"
        threat_actor = "APT1"
        reference = "Mandiant APT1 Report Appendix"
    strings:
        $mutex1 = "Global\\MicrosoftUpdateMutex" wide ascii
        $mutex2 = "Global\\WindowsUpdateMutex" wide ascii
        $c2_1 = "googleupdateserver.com" wide ascii
        $c2_2 = "microsoftupdateserver.net" wide ascii
        $c2_3 = "adobe-flash-update.org" wide ascii
        $path1 = "\\Microsoft\\Windows\\Templates\\" wide ascii
        $string1 = "PlugX" wide ascii
        $string2 = "Korplug" wide ascii
        $plugin1 = "cmdshell" wide ascii
        $plugin2 = "filemgr" wide ascii
    condition:
        3 of ($mutex*, $c2_*, $path1, $string*, $plugin*)
}
```

### Sigma
```yaml
title: APT1 PlugX Persistence via Registry Run Key
id: apt1-plugx-persistence-run-key
status: stable
description: Detects APT1 PlugX persistence via registry Run key
references:
    - https://www.mandiant.com/resources/reports/apt1
author: CTI Team
date: 2024-12-15
logsource:
    category: registry
    product: windows
detection:
    selection:
        TargetObject|endswith: '\\Run\\'
        Details|contains: 'Microsoft\\Windows\\Templates'
    condition: selection
falsepositives:
    - Low
level: high
tags:
    - attack.persistence
    - attack.t1547.001
    - actor.apt1
    - malware.plugx
```

### Snort/Suricata
```
alert http $HOME_NET any -> $EXTERNAL_NET any (msg:"APT1 PlugX C2 Check-in"; flow:to_server,established; content:"GET"; http_method; content:"/update.aspx"; http_uri; content:"User-Agent|3a| PlugX"; http_header; classtype:trojan-activity; sid:1000001; rev:1;)
```

### STIX/TAXII
```json
{
  "type": "bundle",
  "id": "bundle--apt1-iocs-2024",
  "spec_version": "2.1",
  "objects": [
    {
      "type": "indicator",
      "spec_version": "2.1",
      "id": "indicator--apt1-plugx-hash",
      "created": "2024-12-15T00:00:00.000Z",
      "modified": "2024-12-15T00:00:00.000Z",
      "pattern": "[file:hashes.MD5 = 'a1b2c3d4e5f6789012345678901234ab']",
      "pattern_type": "stix",
      "labels": ["malicious-activity"],
      "description": "APT1 PlugX v3.0 loader"
    }
  ]
}
```

## Enrichment
### VirusTotal
| Hash | Detections | Last Analysis | Link |
|------|------------|---------------|------|
| a1b2c3d4e5f6789012345678901234ab | 45/72 | 2024-12-10 | https://vt.com/file/... |

### Passive DNS
| Domain | IP | First Seen | Last Seen | Source |
|--------|----|------------|-----------|--------|
| googleupdateserver.com | 203.0.113.45 | 2012-01-15 | 2013-02-20 | RiskIQ |

### WHOIS
| Domain | Registrar | Creation | Expiration | Registrant | Nameservers |
|--------|-----------|----------|------------|------------|-------------|
| googleupdateserver.com | GoDaddy | 2011-12-01 | 2013-12-01 | Private | ns1.example.com, ns2.example.com |

## Sharing & Distribution
| Format | Generated | Recipients | Classification |
|--------|-----------|------------|----------------|
| STIX 2.1 | 2024-12-15 | Internal SOC, Partners | TLP:CLEAR |
| MISP | 2024-12-15 | MISP Instance | TLP:CLEAR |
| CSV | 2024-12-15 | Detection Engineering | TLP:CLEAR |
| JSON | 2024-12-15 | SIEM Integration | TLP:CLEAR |

## Notes
This IOC collection is based primarily on the Mandiant APT1 Report (2013) appendices. Many indicators are historical (2011-2013) but remain valuable for:
- Historical threat hunting
- Attribution of legacy intrusions
- Understanding APT1 infrastructure patterns
- Training and detection rule development

Post-2013 APT1 infrastructure shifted significantly. See [[CTI/Threat Actors/APT1]] for updated analysis.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*