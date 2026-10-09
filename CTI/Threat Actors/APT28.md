---
aliases: ["Fancy Bear", "Sofacy", "Sednit", "STRONTIUM", "APT28", "Pawn Storm"]
tags: [threat-actor, apt, russia]
type: APT
actor_type: APT
origin: Russia
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
campaigns:
  - "[[CTI/Campaigns/SolarWinds Supply Chain Attack]]"
  - "[[CTI/Campaigns/US Election Interference 2016]]"
  - "[[CTI/Campaigns/German Bundestag Hack 2015]]"
  - "[[CTI/Campaigns/NotPetya 2017]]"
  - "[[CTI/Campaigns/Olympic Destroyer 2018]]"
malware:
  - "[[CTI/Malware/X-Agent]]"
  - "[[CTI/Malware/Zebrocy]]"
  - "[[CTI/Malware/Cobalt Strike]]"
tools:
  - "[[CTI/Tools/Mimikatz]]"
  - "[[CTI/Tools/Responder]]"
---

# APT28 - Threat Actor Profile

## Overview
- **Name:** APT28
- **Aliases:** Fancy Bear, Sofacy, Sednit, STRONTIUM, Pawn Storm
- **Type:** APT (Advanced Persistent Threat)
- **Origin/Country:** Russia (GRU Unit 26165/74455)
- **First Observed:** 2004
- **Last Activity:** 2024
- **Status:** active
- **Confidence Level:** high

## Description
APT28 is a Russian military intelligence (GRU) cyber espionage group active since at least 2004. They are known for high-profile operations including the 2016 US election interference, 2015 German Bundestag hack, 2017 NotPetya, and 2018 Olympic Destroyer. The group uses a diverse malware arsenal including X-Agent, X-Tunnel, Zebrocy, and numerous custom tools.

## Goals & Motivation
- **Primary Goal:** Strategic intelligence collection, political influence operations
- **Secondary Goals:** Disruption, destructive attacks, credential theft
- **Motivation:** Nation-state sponsored espionage and influence operations

## Targeting
### Sectors Targeted
- Government, Military, Defense Contractors, Political Organizations, Media, Energy, Aerospace, Sports Organizations (anti-doping), NGOs, Think Tanks

### Geographic Targeting
- NATO countries, Eastern Europe, Caucasus, Central Asia, United States, Western Europe, Ukraine, Georgia

### Notable Victims
- Democratic National Committee (2016), German Bundestag (2015), WADA (2016), Olympics (2018), Ukrainian artillery units (2014-2016), COVID-19 vaccine researchers (2020-2021)

## Capabilities & Resources
- **Sophistication Level:** advanced
- **Funding Source:** Russian government (GRU)
- **Team Size:** Large, organized in units
- **Infrastructure:** Global infrastructure, compromised routers/VPNs, anonymization networks

## TTPs (MITRE ATT&CK Mapping)
| Technique ID | Technique Name | Description | Sub-techniques |
|--------------|----------------|-------------|----------------|
| T1566.001 | Phishing: Spearphishing Attachment | Primary initial access with malicious docs | .001, .002 |
| T1566.002 | Phishing: Spearphishing Link | Credential harvesting via phishing links | |
| T1190 | Exploit Public-Facing Application | VPN/Exchange/SharePoint exploitation | |
| T1059.001 | Command and Scripting Interpreter: PowerShell | Heavy PowerShell usage | |
| T1059.003 | Command and Scripting Interpreter: Windows Command Shell | | |
| T1055.012 | Process Injection: Process Hollowing | X-Agent injection techniques | |
| T1021.004 | Remote Services: Pass the Hash | Lateral movement | |
| T1003.001 | OS Credential Dumping: LSASS Memory | Mimikatz, custom dumpers | |
| T1550.002 | Use Alternate Authentication Material: Pass the Hash | | |
| T1070.004 | Indicator Removal: File Deletion | Anti-forensics | |
| T1497.001 | Virtualization/Sandbox Evasion: System Checks | VM detection in malware | |
| T1027.002 | Obfuscated Files or Information: Software Packing | Custom packers | |
| T1573.001 | Encrypted Channel: Symmetric Cryptography | Custom C2 encryption | |
| T1090.003 | Proxy: Multi-hop Proxy | Router/VPN compromise for proxy chains | |

> **Related TTPs:** [[CTI/TTPs/]]

## Malware & Tools Used
| Malware/Tool | Type | Description | Links |
|--------------|------|-------------|-------|
| X-Agent (CHOPSTICK) | RAT | Cross-platform (Windows, Linux, iOS, Android) | [[CTI/Malware/X-Agent]] |
| X-Tunnel | Proxy/Tunneling | Traffic forwarding tool | [[CTI/Tools/X-Tunnel]] |
| Zebrocy | Downloader/Backdoor | Delphi/Go variants, modular | [[CTI/Malware/Zebrocy]] |
| SPLM (Second Stage) | Backdoor | Lightweight second-stage implant | |
| GAMEFISH | Backdoor | Linux/iOS targeting | |
| Mimikatz | Credential Theft | Credential dumping | [[CTI/Tools/Mimikatz]] |
| Responder | LLMNR/NBT-NS Poisoning | Network credential harvesting | [[CTI/Tools/Responder]] |
| Custom Exploits | Exploit | CVE-2023-23397, CVE-2022-41040/41082, etc. | |

> **See also:** [[CTI/Malware/]], [[CTI/Tools/]]

## Infrastructure & IOCs
### Command & Control
- **C2 Domains:** Dynamic DNS, compromised domains, typosquatting (e.g., `microsoft-online.com`, `office365-security.com`)
- **C2 IPs:** Compromised routers (Ubiquiti, Cisco), VPS, Tor exit nodes
- **Protocols:** HTTP/HTTPS, custom binary protocols, DNS tunneling

### Host-Based IOCs
- **File Hashes:** 500+ samples across malware families
- **Registry Keys:** Run keys, services, WMI event subscriptions
- **Mutexes:** `Global\XAgentMutex`, `ZebrocyMutex`
- **File Paths:** `%APPDATA%\Microsoft\Windows\`, `%ProgramData%\`

### Network IOCs
- **IP Addresses:** Compromised edge devices globally
- **Domains:** Typosquatting, dynamic DNS (no-ip, dynv6, duckdns)
- **URLs:** `/api/`, `/v1/`, `/sync/`, `/update/` API-like paths

> **Full IOC List:** [[CTI/IOCs/APT28 IOCs]]

## Associated Campaigns
- [[CTI/Campaigns/US Election Interference 2016]]
- [[CTI/Campaigns/German Bundestag Hack 2015]]
- [[CTI/Campaigns/NotPetya 2017]]
- [[CTI/Campaigns/Olympic Destroyer 2018]]
- [[CTI/Campaigns/COVID-19 Vaccine Research Targeting 2020]]
- [[CTI/Campaigns/Ukraine Targeting 2022-2024]]

## Attribution & Relationships
- **Attributed To:** GRU Unit 26165 (fancy bear) and Unit 74455 (Sandworm overlap) - US DOJ, UK NCSC, Dutch AIVD
- **Related Actors:** Sandworm (APT44/VOODOO BEAR) - overlap in infrastructure/tools, Turla - occasional cooperation
- **Collaborations:** Coordinates with IRA (Internet Research Agency) for influence operations

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| US DOJ | Indictment | 2018-07-13 | A | https://www.justice.gov/opa/pr/grand-jury-indicts-twelve-russian-intelligence-officers |
| UK NCSC | Advisory | 2018-10-04 | A | https://www.ncsc.gov.uk/news/russian-intelligence-cyber-attacks |
| CrowdStrike | Report | 2016-2024 | A | https://www.crowdstrike.com/blog/ |
| FireEye/Mandiant | Reports | 2014-2024 | A | https://www.mandiant.com/resources |
| Microsoft | Threat Intelligence | 2020-2024 | A | https://www.microsoft.com/en-us/security/business/threat-intelligence |
| MITRE ATT&CK | Framework | 2024 | A | https://attack.mitre.org/groups/G0007/ |

## Notes & Analysis
APT28 is one of the most sophisticated and destructive APT groups. Key characteristics:
- **Dual mission:** Espionage + destructive/influence operations
- **Rapid exploitation:** Weaponizes 0-days and n-days within hours/days (CVE-2023-23397 exploited within hours)
- **Operational security:** Compartmentalized infrastructure per operation
- **Cross-platform:** Windows, Linux, macOS, iOS, Android, network devices
- **Router compromise:** Unique focus on compromising edge networking equipment for anonymization

The group shows clear GRU sponsorship with military-style organization (Unit 26165 for cyber ops, Unit 74455 for destructive ops).

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*