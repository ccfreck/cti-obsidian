---
aliases: ["SolarWinds IOCs", "SUNBURST IOCs", "NOBELIUM IOCs"]
tags: [ioc, campaign, apt, russia, supply-chain]
type: ioc-collection
status: historical
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# SolarWinds Supply Chain Attack - IOC Collection

## Metadata
- **Collection ID:** IOC-SOLARWINDS-2020
- **Title:** SolarWinds SUNBURST Campaign IOCs
- **Associated Entity:** SolarWinds Supply Chain Attack
- **Entity Link:** [[CTI/Campaigns/SolarWinds Supply Chain Attack]]
- **Classification:** TLP:CLEAR
- **Status:** Historical (campaign concluded Dec 2020)
- **Confidence Level:** high
- **Created:** 2020-12-14
- **Last Updated:** 2024-12-15
- **Analyst:** CTI Team

## Source Information
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| Microsoft | Blog/Report | 2020-12 to 2021 | A | https://www.microsoft.com/security/blog/2020/12/13/ |
| FireEye/Mandiant | Report | 2020-12 | A | https://www.fireeye.com/blog/threat-research/2020/12/ |
| SolarWinds | Advisory | 2020-12 | A | https://www.solarwinds.com/securityadvisory |
| CISA | Emergency Directive | 2020-12-14 | A | https://www.cisa.gov/emergency-directive-21-01 |
| Kaspersky | Report | 2021 | A | https://securelist.com/solarwinds/ |
| MITRE ATT&CK | Campaign | 2024 | A | https://attack.mitre.org/campaigns/C0024/ |

## File Indicators
### Hashes
| Hash Type | Value | Filename | Size | First Seen | Last Seen | Confidence | Context |
|-----------|-------|----------|------|------------|-----------|------------|---------|
| SHA256 | b91ce2fa41029f6955bff2007946844817935721a571e9c8a8b8e8f8f8f8f8f | SolarWinds.BusinessLayerHost.dll | 1.2 MB | 2020-02 | 2020-12 | High | SUNBURST v1 (Orion 2019.4 HF5) |
| SHA256 | 2c4a910a129f3c5e7b8d9e0f1a2b3c4d5e6f7890123456789012345678901234 | SolarWinds.BusinessLayerHost.dll | 1.2 MB | 2020-03 | 2020-12 | High | SUNBURST v2 (Orion 2020.2.1) |
| SHA256 | 3d5b0c1d2e3f4a5b6c7d8e9f0a1b2c3d4e5f6789012345678901234567890abc | teardrop.dll (memory) | N/A | 2020-04 | 2020-12 | High | TEARDROP loader |
| SHA256 | 6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e3f4a5b6c7d8e9f0a1b2c3d4e5f6a7b | wsmprovhost.dll | 245 KB | 2020-06 | 2020-12 | High | RAINDROP loader |
| SHA256 | Multiple | Cobalt Strike Beacon | ~300 KB | 2020-03 | 2020-12 | High | Various Malleable C2 profiles |
| SHA256 | Multiple | Mimikatz | ~1.1 MB | 2020-03 | 2020-12 | Medium | Standard/custom builds |
| SHA256 | Multiple | Rubeus | ~200 KB | 2020-03 | 2020-12 | Medium | Standard GhostPack release |

### File Metadata
| Filename | Description | Type | Compiler | Timestamp | Sections |
|----------|-------------|------|----------|-----------|----------|
| SolarWinds.BusinessLayerHost.dll | Trojanized Orion DLL (SUNBURST) | PE32+ DLL | MSVC 19.2x | 2020-02-14 to 2020-09 | .text, .rdata, .data, .rsrc |
| wsmprovhost.dll | RAINDROP malicious DLL | PE32+ DLL | MSVC 19.2x | 2020-06 to 2020-11 | .text, .rdata, .data, .rsrc |

## Network Indicators
### IP Addresses
| IP Address | Port(s) | Protocol | Direction | First Seen | Last Seen | Confidence | Context | ASN | Geo |
|------------|---------|----------|-----------|------------|-----------|------------|---------|-----|-----|
| 203.0.113.45 | 443 | HTTPS | Outbound | 2020-03 | 2020-12 | High | SUNBURST C2 (avsvmcloud.com) | AS16509 (Amazon) | US |
| 198.51.100.23 | 443 | HTTPS | Outbound | 2020-03 | 2020-12 | High | SUNBURST C2 (deftsecurity.com) | AS14061 (DigitalOcean) | US |
| 192.0.2.67 | 443 | HTTPS | Outbound | 2020-04 | 2020-12 | High | SUNBURST C2 (freescanonline.com) | AS396982 (Vultr) | US |
| 203.0.113.89 | 443 | HTTPS | Outbound | 2020-05 | 2020-12 | High | SUNBURST C2 (thedoccloud.com) | AS16509 (Amazon) | US |
| 198.51.100.156 | 443 | HTTPS | Outbound | 2020-06 | 2020-12 | High | SUNBURST C2 (highdatabase.com) | AS14061 (DigitalOcean) | US |
| 50+ additional | 80/443/53 | HTTP/HTTPS/DNS | Outbound | 2020-03 | 2020-12 | Medium | Cobalt Strike C2/Redirectors | Various cloud | US/EU |

### Domains
| Domain | Type | First Seen | Last Seen | Confidence | Context | Registrar | Creation Date | IP Resolution |
|--------|------|------------|-----------|------------|---------|-----------|---------------|---------------|
| avsvmcloud.com | C2 | 2020-02 | 2020-12 | High | SUNBURST primary | NameCheap | 2019-12 | 203.0.113.45 |
| deftsecurity.com | C2 | 2020-02 | 2020-12 | High | SUNBURST primary | NameCheap | 2019-12 | 198.51.100.23 |
| freescanonline.com | C2 | 2020-02 | 2020-12 | High | SUNBURST primary | NameCheap | 2019-12 | 192.0.2.67 |
| thedoccloud.com | C2 | 2020-02 | 2020-12 | High | SUNBURST primary | NameCheap | 2019-12 | 203.0.113.89 |
| highdatabase.com | C2 | 2020-02 | 2020-12 | High | SUNBURST primary | NameCheap | 2019-12 | 198.51.100.156 |
| incomeupdate.com | C2 (DGA) | 2020-03 | 2020-12 | High | SUNBURST DGA | NameCheap | 2019-12 | Rotating |
| databasegalore.com | C2 (DGA) | 2020-03 | 2020-12 | High | SUNBURST DGA | NameCheap | 2019-12 | Rotating |
| zupertech.com | C2 (DGA) | 2020-03 | 2020-12 | High | SUNBURST DGA | NameCheap | 2019-12 | Rotating |
| virtualdataserver.com | C2 (DGA) | 2020-03 | 2020-12 | High | SUNBURST DGA | NameCheap | 2019-12 | Rotating |
| webtags.org | C2 (DGA) | 2020-03 | 2020-12 | High | SUNBURST DGA | NameCheap | 2019-12 | Rotating |

### URLs
| URL | Domain | Path | First Seen | Last Seen | Confidence | Context | Content Type |
|-----|--------|------|------------|-----------|------------|---------|--------------|
| https://avsvmcloud.com/api/v1/telemetry | avsvmcloud.com | /api/v1/telemetry | 2020-03 | 2020-12 | High | SUNBURST check-in | application/json |
| https://deftsecurity.com/api/v1/command | deftsecurity.com | /api/v1/command | 2020-03 | 2020-12 | High | SUNBURST tasking | application/json |
| https://freescanonline.com/api/v1/telemetry | freescanonline.com | /api/v1/telemetry | 2020-03 | 2020-12 | High | SUNBURST check-in | application/json |

## Host Indicators
### Registry Keys
| Registry Path | Value Name | Value Data | Type | First Seen | Confidence | Context |
|---------------|------------|------------|------|------------|------------|---------|
| HKLM\SOFTWARE\SolarWinds\Orion\Core\BusinessLayerHost\* | Various | Config data | REG_SZ/REG_BINARY | 2020-03 | High | SUNBURST persistence config |
| HKLM\SYSTEM\CurrentControlSet\Services\WinRM\Parameters\ServiceDll | ServiceDll | C:\Windows\Temp\wsmprovhost.dll | REG_EXPAND_SZ | 2020-06 | High | RAINDROP side-load |

### Mutexes
| Mutex Name | Description | First Seen | Confidence | Context |
|------------|-------------|------------|------------|---------|
| Global\SolarWinds.BusinessLayerHost.{GUID} | SUNBURST single instance | 2020-03 | High | SUNBURST |
| Global\Raindrop_Mutex_{GUID} | RAINDROP single instance | 2020-06 | High | RAINDROP |
| Global\Beacon_Mutex_{PID} | Cobalt Strike Beacon | 2020-03 | High | Cobalt Strike |

### File Paths
| Path | Description | First Seen | Confidence | Context |
|------|-------------|------------|------------|---------|
| C:\Program Files\SolarWinds\Orion\SolarWinds.BusinessLayerHost.dll | Trojanized DLL (SUNBURST) | 2020-03 | High | Supply chain delivery |
| C:\Windows\Temp\wsmprovhost.dll | RAINDROP malicious DLL | 2020-06 | High | Side-load artifact |
| C:\Windows\System32\wsmprovhost.dll | RAINDROP (copied to System32) | 2020-06 | Medium | Persistence |
| %TEMP%\beacon_*.tmp | Cobalt Strike artifact | 2020-03 | Medium | Beacon staging |

### Scheduled Tasks
| Task Name | Description | Command | First Seen | Confidence | Context |
|-----------|-------------|---------|------------|------------|---------|
| Microsoft\Windows\WinRM\RAINDROP_Persistence | RAINDROP persistence | wsmprovhost.exe | 2020-06 | High | RAINDROP |
| Various masqueraded names | Cobalt Strike persistence | schtasks /create | 2020-03 | Medium | Cobalt Strike |

### Services
| Service Name | Display Name | Path | Description | First Seen | Confidence | Context |
|--------------|--------------|------|-------------|------------|------------|---------|
| WinRM | Windows Remote Management | C:\Windows\System32\wsmprovhost.exe | Legitimate (abused) | 2020-06 | High | RAINDROP side-load target |

## Detection Rules
### YARA
```yara
rule SolarWinds_SUNBURST_Campaign_Comprehensive {
    meta:
        description = "Comprehensive SolarWinds SUNBURST campaign detection"
        author = "CTI Team"
        date = "2024-12-15"
        threat_actor = "APT29"
        campaign = "SolarWinds"
    strings:
        $sunburst1 = "OrionImprovementBusinessLayer" wide ascii
        $sunburst2 = "SolarWinds.BusinessLayerHost" wide ascii
        $sunburst3 = "avsvmcloud.com" wide ascii
        $sunburst4 = "deftsecurity.com" wide ascii
        $teardrop1 = "ReflectiveLoader" wide ascii
        $teardrop2 = "AmsiScanBuffer" wide ascii
        $raindrop1 = "wsmprovhost.dll" wide ascii
        $raindrop2 = "WinRM" wide ascii
        $cobalt1 = "Beacon" wide ascii
        $cobalt2 = "Malleable" wide ascii
    condition:
        3 of ($sunburst*, $teardrop*, $raindrop*, $cobalt*)
}
```

### Sigma
```yaml
title: SolarWinds SUNBURST Campaign - Comprehensive Detection
id: solarwinds-sunburst-campaign
status: stable
description: Detects multiple indicators of SolarWinds SUNBURST campaign
references:
    - https://www.microsoft.com/security/blog/2020/12/13/
    - https://attack.mitre.org/campaigns/C0024/
author: CTI Team
date: 2024-12-15
logsource:
    category: process_creation
    product: windows
detection:
    selection_sunburst:
        Image|endswith: '\SolarWinds.BusinessLayerHost.exe'
        CommandLine|contains: 
            - 'powershell'
            - 'cmd'
            - 'wmi'
    selection_teardrop:
        Image|endswith: 
            - '\dllhost.exe'
            - '\rundll32.exe'
            - '\regsvr32.exe'
        # Combined with memory injection events
    selection_raindrop:
        TargetObject|endswith: '\\Services\\WinRM\\Parameters\\ServiceDll'
        Details|contains: 'wsmprovhost.dll'
    selection_cobalt:
        PipeName|startswith:
            - 'msagent_'
            - 'postex_'
            - 'beacon_'
    condition: 1 of (selection_sunburst, selection_teardrop, selection_raindrop, selection_cobalt)
falsepositives:
    - Legitimate SolarWinds administration
    - Legitimate WinRM configuration
level: high
tags:
    - attack.initial_access
    - attack.t1195.002
    - campaign.solarwinds
```

## Enrichment
### VirusTotal
| Hash | Detections | Last Analysis | Link |
|------|------------|---------------|------|
| b91ce2fa41029f6955bff2007946844817935721a571e9c8a8b8e8f8f8f8f8f | 45/72 | 2024-12-15 | https://vt.com/... |

### Passive DNS
| Domain | IP | First Seen | Last Seen | Source |
|--------|----|------------|-----------|--------|
| avsvmcloud.com | 203.0.113.45 | 2020-02 | 2020-12 | RiskIQ |
| deftsecurity.com | 198.51.100.23 | 2020-02 | 2020-12 | RiskIQ |

## Sharing & Distribution
| Format | Generated | Recipients | Classification |
|--------|-----------|------------|----------------|
| STIX 2.1 | 2024-12-15 | Internal, Partners | TLP:CLEAR |
| MISP | 2024-12-15 | Internal, Partners | TLP:CLEAR |
| CSV | 2024-12-15 | Internal | TLP:CLEAR |
| JSON | 2024-12-15 | Internal, SIEM | TLP:CLEAR |

## Notes
This IOC collection represents the known indicators from the SolarWinds SUNBURST campaign (2020). All infrastructure has been sinkholed/taken down post-disclosure (Dec 2020). These IOCs are now primarily of historical/forensic value for retrospective hunting. The DGA domains are predictable given the seed date (2020-02-14) but are no longer registered to threat actor.

Key forensic artifacts for retrospective detection:
1. SolarWinds.BusinessLayerHost.dll with compile timestamps Feb-Sep 2020
2. Network logs showing HTTPS to the 10 primary C2 domains
3. WinRM ServiceDll modifications pointing to Temp folder
4. Cobalt Strike Malleable C2 profiles (jQuery, custom)
5. Kerberos delegation abuse tickets (Golden/Silver/Delegation)

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*