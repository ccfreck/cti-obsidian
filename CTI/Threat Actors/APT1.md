---
aliases: ["Comment Crew", "Comment Panda", "GIF89a", "BrownFox"]
tags: [threat-actor, apt, china]
type: threat-actor
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# APT1 - Threat Actor Profile

## Overview
- **Name:** APT1
- **Aliases:** Comment Crew, Comment Panda, GIF89a, BrownFox
- **Type:** APT (Advanced Persistent Threat)
- **Origin/Country:** China (People's Liberation Army Unit 61398)
- **First Observed:** 2006
- **Last Activity:** 2023
- **Status:** active
- **Confidence Level:** high

## Description
APT1 is a Chinese military unit (PLA Unit 61398) responsible for extensive cyber espionage operations targeting organizations across multiple industries worldwide. Mandiant's 2013 report "APT1: Exposing One of China's Cyber Espionage Units" brought significant public attention to this group. They are known for their persistent, long-term campaigns targeting intellectual property and sensitive business information.

## Goals & Motivation
- **Primary Goal:** Intellectual property theft and economic espionage
- **Secondary Goals:** Strategic intelligence gathering, competitive advantage for Chinese state-owned enterprises
- **Motivation:** Nation-state sponsored economic espionage

## Targeting
### Sectors Targeted
- Aerospace, Computer Software, Information Technology, Telecommunications, Electronics, Energy, Engineering, Healthcare, Metallurgy, Satellites, Scientific Research

### Geographic Targeting
- Primarily United States, Canada, United Kingdom, Japan, Taiwan, and other NATO countries

### Notable Victims
- 141+ organizations compromised (per Mandiant 2013 report)
- Major corporations across 20+ industries

## Capabilities & Resources
- **Sophistication Level:** advanced
- **Funding Source:** Chinese government/military (PLA)
- **Team Size:** Hundreds of operators (estimated)
- **Infrastructure:** Extensive dedicated infrastructure including thousands of C2 domains and IPs

## TTPs (MITRE ATT&CK Mapping)
| Technique ID | Technique Name | Description | Sub-techniques |
|--------------|----------------|-------------|----------------|
| T1566.001 | Phishing: Spearphishing Attachment | Primary initial access vector using malicious attachments | .001, .002, .003 |
| T1059.003 | Command and Scripting Interpreter: Windows Command Shell | Extensive use of cmd.exe for execution | |
| T1059.001 | Command and Scripting Interpreter: PowerShell | Increasing use of PowerShell in later campaigns | |
| T1021.004 | Remote Services: Pass the Hash | Lateral movement using stolen credentials | |
| T1003.001 | OS Credential Dumping: LSASS Memory | Credential theft via Mimikatz and custom tools | |
| T1082 | System Information Discovery | Extensive reconnaissance post-compromise | |
| T1083 | File and Directory Discovery | Data staging and collection | |
| T1005 | Data from Local System | Collection of documents, emails, source code | |
| T1041 | Exfiltration Over Command and Control Channel | Data exfiltration via existing C2 channels | |
| T1573.001 | Encrypted Channel: Symmetric Cryptography | Custom encryption for C2 communications | |

> **Related TTPs:** [[CTI/TTPs/]]

## Malware & Tools Used
| Malware/Tool | Type | Description | Links |
|--------------|------|-------------|-------|
| PlugX | RAT | Modular remote access trojan, primary implant | [[CTI/Malware/PlugX]] |
| PoisonIvy | RAT | Legacy RAT used in early campaigns | [[CTI/Malware/PoisonIvy]] |
| Gh0st RAT | RAT | Open-source RAT variant used by APT1 | [[CTI/Malware/Gh0st RAT]] |
| Mimikatz | Credential Theft | Credential dumping utility | [[CTI/Tools/Mimikatz]] |
| Custom Tools | Various | Dozens of custom backdoors, downloaders, utilities | [[CTI/Malware/APT1 Custom Tools]] |

> **See also:** [[CTI/Malware/]], [[CTI/Tools/]]

## Infrastructure & IOCs
### Command & Control
- **C2 Domains:** 1000+ domains registered (e.g., `googleupdateserver.com`, `microsoftupdateserver.net`)
- **C2 IPs:** Hundreds of dedicated VPS/hosted IPs, primarily in US hosting providers
- **Protocols:** HTTP/HTTPS with custom encryption, custom TCP protocols

### Host-Based IOCs
- **File Hashes:** 3000+ malware samples documented (MD5/SHA1/SHA256)
- **Registry Keys:** `HKCU\Software\Microsoft\Windows\CurrentVersion\Run` persistence
- **Mutexes:** `Global\MicrosoftUpdateMutex`, `Global\WindowsUpdateMutex`
- **File Paths:** `%APPDATA%\Microsoft\Windows\Templates\`, `%TEMP%\~*.tmp`

### Network IOCs
- **IP Addresses:** 200+ C2 IPs (see Mandiant Appendix C)
- **Domains:** 1000+ C2 domains (see Mandiant Appendix B)
- **URLs:** `/update.aspx`, `/check.aspx`, `/download.aspx` patterns

> **Full IOC List:** [[CTI/IOCs/APT1 IOCs]]

## Associated Campaigns
- [[CTI/Campaigns/Operation Aurora]] (possible involvement)
- [[CTI/Campaigns/APT1 2006-2013 Campaign]]
- [[CTI/Campaigns/APT1 Post-2013 Activity]]

## Attribution & Relationships
- **Attributed To:** PLA Unit 61398 (Shanghai, China) - Mandiant, US DOJ
- **Related Actors:** APT3 (Buckeye), APT5, APT17 (DeputyDog) - shared infrastructure/malware
- **Collaborations:** Shares infrastructure with other PLA units

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| Mandiant | Report | 2013-02-19 | A | https://www.mandiant.com/resources/reports/apt1 |
| US DOJ | Indictment | 2014-05-19 | A | https://www.justice.gov/opa/pr/us-charges-five-chinese-military-hackers |
| FireEye | Blog | 2015-2023 | A | https://www.fireeye.com/blog/threat-research.html |
| MITRE ATT&CK | Framework | 2024 | A | https://attack.mitre.org/groups/G0006/ |

## Notes & Analysis
APT1 remains one of the most documented and prolific Chinese APT groups. Post-2013 exposure, they temporarily reduced activity but resumed operations with improved OPSEC. Their malware ecosystem (PlugX, custom tools) continues to evolve. The group demonstrates the "smash and grab" approach - broad targeting, rapid exploitation, bulk data exfiltration.

Key evolution post-2013:
- Increased use of legitimate tools (living-off-the-land)
- Better operational security (less reused infrastructure)
- More targeted spearphishing
- Shift toward cloud/hosted infrastructure

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*