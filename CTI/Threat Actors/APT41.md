---
aliases: ["WICKED PANDA", "Winnti Group", "Barium", "APT41", "Double Dragon", "RedGolf"]
tags: [threat-actor, apt, china, cybercrime]
type: APT
actor_type: APT
origin: China
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
campaigns:
  - "[[CTI/Campaigns/Winnti Supply Chain 2013-2019]]"
  - "[[CTI/Campaigns/APT41 2020 Campaign]]"
  - "[[CTI/Campaigns/Log4j Exploitation 2021]]"
malware:
  - "[[CTI/Malware/PlugX]]"
  - "[[CTI/Malware/ShadowPad]]"
  - "[[CTI/Malware/Cobalt Strike]]"
tools:
  - "[[CTI/Tools/Mimikatz]]"
  - "[[CTI/Tools/Sqlmap]]"
---

# APT41 - Threat Actor Profile

## Overview
- **Name:** APT41
- **Aliases:** WICKED PANDA, Winnti Group, Barium, Double Dragon, RedGolf
- **Type:** APT / Cybercrime (dual mission)
- **Origin/Country:** China (Ministry of State Security contractors)
- **First Observed:** 2012 (Winnti), 2014 (APT41 designation)
- **Last Activity:** 2024
- **Status:** active
- **Confidence Level:** high

## Description
APT41 is a Chinese state-sponsored threat group that conducts both cyber espionage and financially motivated cybercrime operations. Uniquely, they run "moonlighting" operations - using state-sponsored capabilities for personal profit (ransomware, cryptojacking, game currency theft) while also conducting strategic intelligence collection for the Chinese MSS. US DOJ indicted 5 members in 2020.

## Goals & Motivation
- **Primary Goal:** State-sponsored espionage (intellectual property, strategic intelligence)
- **Secondary Goals:** Financial gain (ransomware, cryptojacking, supply chain monetization)
- **Motivation:** Dual mission - MSS tasking + personal profit

## Targeting
### Sectors Targeted
- **Espionage:** Telecommunications, Healthcare, High-Tech, Media, Pharmaceutical, Retail, Education, Government
- **Cybercrime:** Video Game Industry, Cryptocurrency, Financial Services, Supply Chain (software vendors)

### Geographic Targeting
- Global: US, UK, Japan, South Korea, Hong Kong, Taiwan, India, Southeast Asia, Europe, South America

### Notable Victims
- 100+ organizations across espionage campaigns
- Video game companies (supply chain compromises)
- Healthcare orgs (COVID-19 research)
- Telecom providers (metadata collection)

## Capabilities & Resources
- **Sophistication Level:** advanced
- **Funding Source:** Chinese MSS + cybercrime revenue
- **Team Size:** 5+ indicted individuals, larger contractor network
- **Infrastructure:** Compromised infrastructure, cloud hosting, supply chain

## TTPs (MITRE ATT&CK Mapping)
| Technique ID | Technique Name | Description | Sub-techniques |
|--------------|----------------|-------------|----------------|
| T1195.002 | Supply Chain Compromise: Software Supply Chain | Compromised build systems, software updates | .001, .002 |
| T1566.001 | Phishing: Spearphishing Attachment | Targeted phishing with custom malware | |
| T1190 | Exploit Public-Facing Application | Heavy exploitation of web apps (Log4j, ProxyLogon, etc.) | |
| T1059.001 | PowerShell | Extensive PowerShell usage | |
| T1059.005 | Visual Basic | VBScript/VBA in phishing docs | |
| T1027.002 | Obfuscated Files: Software Packing | Custom packers (VMProtect, custom) | |
| T1574.001 | Hijack Execution Flow: DLL Search Order Hijacking | DLL sideloading extensively used | .001, .002 |
| T1055.012 | Process Injection: Process Hollowing | | |
| T1003.001 | OS Credential Dumping: LSASS Memory | | |
| T1556.002 | Credential Theft: Password Filter | Custom password filters | |
| T1497.001 | Virtualization/Sandbox Evasion | Extensive anti-analysis | |
| T1573.001 | Encrypted Channel: Symmetric Cryptography | Custom C2 encryption | |
| T1071.001 | Application Layer Protocol: Web Protocols | HTTP/HTTPS C2 | |
| T1568.002 | Dynamic Resolution: Domain Generation Algorithms | DGAs in multiple families | |

> **Related TTPs:** [[CTI/TTPs/]]

## Malware & Tools Used
| Malware/Tool | Type | Description | Links |
|--------------|------|-------------|-------|
| PlugX | RAT | Shared with other Chinese groups | [[CTI/Malware/PlugX]] |
| ShadowPad | Backdoor | Modular, plugin-based backdoor | [[CTI/Malware/ShadowPad]] |
| Cobalt Strike | C2 Framework | Legitimate tool abused extensively | [[CTI/Tools/Cobalt Strike]] |
| Mimikatz | Credential Theft | | [[CTI/Tools/Mimikatz]] |
| DEADEYE | Loader | Custom loader | |
| KEYPLUG | Backdoor | Linux/Windows variants | [[CTI/Malware/KEYPLUG]] |
| DUSTPAN | Downloader | | |
| DUSTTRAP | Backdoor | | |
| Sqlmap | SQL Injection | Automated SQLi tool | [[CTI/Tools/Sqlmap]] |
| Custom Ransomware | Ransomware | Ransomware deployments (e.g., REvil affiliate) | |

> **See also:** [[CTI/Malware/]], [[CTI/Tools/]]

## Infrastructure & IOCs
### Command & Control
- **C2 Domains:** Compromised legitimate domains, algorithmically generated, cloud storage APIs (GitHub, Google Drive, Dropbox)
- **C2 IPs:** Cloud providers (AWS, Azure, Alibaba Cloud), compromised servers
- **Protocols:** HTTPS, DNS, cloud storage APIs, custom TCP

### Host-Based IOCs
- **File Hashes:** Hundreds across malware families
- **Registry Keys:** DLL sideloading paths, service keys
- **Mutexes:** Family-specific mutexes
- **File Paths:** DLL sideloading locations (`%APPDATA%\`, `%PROGRAMFILES%\`)

### Network IOCs
- **IP Addresses:** Cloud provider ranges
- **Domains:** DGAs, compromised legitimate domains
- **URLs:** Cloud storage API endpoints, `/api/`, `/sync/`

> **Full IOC List:** [[CTI/IOCs/APT41 IOCs]]

## Associated Campaigns
- [[CTI/Campaigns/Winnti Supply Chain 2013-2019]]
- [[CTI/Campaigns/APT41 2020 Campaign]]
- [[CTI/Campaigns/Log4j Exploitation 2021]]
- [[CTI/Campaigns/ProxyLogon Exploitation 2021]]
- [[CTI/Campaigns/Video Game Supply Chain Attacks]]
- [[CTI/Campaigns/COVID-19 Research Targeting 2020]]

## Attribution & Relationships
- **Attributed To:** Chinese MSS contractors (Chengdu 404, etc.) - US DOJ 2020 indictment
- **Related Actors:** APT1 (shared PlugX), APT10 (shared infrastructure), APT17 (shared tools)
- **Collaborations:** Shares malware development ecosystem with other Chinese contractors

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| US DOJ | Indictment | 2020-09-16 | A | https://www.justice.gov/opa/pr/seven-charged-global-cyber-intrusion-campaigns |
| FireEye/Mandiant | Report | 2019-2024 | A | https://www.mandiant.com/resources/blog/apt41-dual-operation |
| Microsoft | Threat Intelligence | 2020-2024 | A | https://www.microsoft.com/en-us/security/business/threat-intelligence |
| Kaspersky | Reports | 2013-2024 | A | https://securelist.com/ |
| MITRE ATT&CK | Framework | 2024 | A | https://attack.mitre.org/groups/G0096/ |

## Notes & Analysis
APT41 is unique in the APT landscape for its explicit dual mission. The 2020 DOJ indictment named 5 individuals (Zhang Haoran, Tan Dailin, Jiang Lizhi, Qian Chuan, Fu Qiang) and a company (Chengdu 404 Network Technology). Their supply chain compromises (CCleaner, ASUS Live Update, NetSarang) demonstrate sophisticated build system infiltration. They rapidly weaponize new vulnerabilities (Log4j within days, ProxyLogon within hours).

Key differentiators:
- **Supply chain mastery:** Multiple high-impact software supply chain attacks
- **Rapid exploitation:** Fastest time-to-exploit for public vulns
- **Moonlighting:** Documented use of state tools for personal profit
- **Cross-platform:** Windows, Linux, macOS, Android, iOS

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*