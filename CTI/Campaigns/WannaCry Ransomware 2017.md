---
aliases: ["WannaCry", "WannaCrypt", "WanaCrypt0r", "WCry"]
tags: [campaign, ransomware, worm, north-korea, global]
type: campaign
status: completed
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# WannaCry Ransomware 2017 - Campaign Profile

## Overview
- **Name:** WannaCry Ransomware 2017
- **Aliases:** WannaCry, WannaCrypt, WanaCrypt0r, WCry
- **Threat Actor(s):** [[CTI/Threat Actors/Lazarus Group]] (Bluenoroff sub-unit)
- **Start Date:** 2017-05-12
- **End Date:** 2017-05-15 (kill switch activated)
- **Status:** completed
- **Confidence Level:** high

## Description
WannaCry was a global ransomware worm that exploited the NSA-leaked ETERNALBLUE exploit (CVE-2017-0144) targeting SMBv1. It infected over 200,000 computers across 150+ countries in 48 hours, causing billions in damages. The attack was halted by a kill switch domain registration. Attributed to North Korea's Lazarus Group (Bluenoroff).

## Objectives
- **Primary Objective:** Financial gain via ransomware ($300-600 Bitcoin per victim)
- **Secondary Objectives:** Disruption, destruction (wiper component in some variants)

## Targeting
### Victims
| Victim | Sector | Country | Compromise Date | Impact |
|--------|--------|---------|-----------------|--------|
| NHS (UK) | Healthcare | UK | 2017-05-12 | 1/3 NHS trusts affected, 19,000 appointments cancelled |
| Telefonica | Telecommunications | Spain | 2017-05-12 | Internal systems encrypted |
| FedEx | Logistics | USA | 2017-05-12 | Systems affected |
| Renault | Automotive | France | 2017-05-12 | Production halted |
| Russian Railways | Transportation | Russia | 2017-05-12 | Systems affected |
| Ministry of Internal Affairs | Government | Russia | 2017-05-12 | 1,000+ computers |
| PetroChina | Energy | China | 2017-05-12 | Payment systems affected |
| Universities | Education | Global | 2017-05-12 | Multiple universities |
| + 200,000+ others | Various | 150+ countries | 2017-05-12 to 2017-05-15 | Varied |

### Geographic Scope
- Global: 150+ countries affected within 48 hours
- Heavily impacted: UK, Russia, Ukraine, India, Taiwan, China, Spain, Italy, Germany, USA

### Sector Focus
- Indiscriminate: Healthcare, Government, Education, Manufacturing, Transportation, Telecommunications, Energy

## Attack Chain (MITRE ATT&CK)
| Phase | Technique ID | Technique Name | Description | Tools/Malware |
|-------|--------------|----------------|-------------|---------------|
| Initial Access | T1190 | Exploit Public-Facing Application | ETERNALBLUE (CVE-2017-0144) SMBv1 exploit | ETERNALBLUE |
| Initial Access | T1190 | Exploit Public-Facing Application | DOUBLEPULSAR backdoor (pre-installed) | DOUBLEPULSAR |
| Execution | T1059.003 | Command and Scripting Interpreter: Windows Command Shell | Ransomware execution, file encryption | WannaCry |
| Persistence | T1547.001 | Boot or Logon Autostart Execution: Registry Run Keys | Persistence via Run keys | WannaCry |
| Privilege Escalation | T1068 | Exploitation for Privilege Escalation | ETERNALBLUE provides SYSTEM | ETERNALBLUE |
| Defense Evasion | T1497.001 | Virtualization/Sandbox Evasion: System Checks | VM detection, sandbox evasion | WannaCry |
| Defense Evasion | T1070.004 | Indicator Removal: File Deletion | Deletes shadow copies, backups | WannaCry (vssadmin) |
| Credential Access | T1003.001 | OS Credential Dumping: LSASS Memory | Not primary (worm spreads via SMB) | - |
| Discovery | T1018 | Remote System Discovery | SMB scanning (port 445) | WannaCry scanner |
| Lateral Movement | T1210 | Exploitation of Remote Services | ETERNALBLUE for worm propagation | ETERNALBLUE |
| Collection | T1005 | Data from Local System | File encryption (targeted extensions) | WannaCry |
| Exfiltration | N/A | N/A | No data exfiltration (pure ransomware) | - |
| Command & Control | T1071.001 | Application Layer Protocol: Web Protocols | HTTP C2 for key retrieval, kill switch check | WannaCry |

## Infrastructure
### Command & Control
- **Domains:** `iuqerfsodp9ifjaposdfjhgosurijfaewrwergwea.com` (kill switch), `ifferfsodp9ifjaposdfjhgosurijfaewrwergwea.com` (variant kill switch)
- **IPs:** Hardcoded IPs for C2 (few, mostly kill switch)
- **Protocols:** HTTP (unencrypted), Tor hidden services for payment

### Delivery Infrastructure
- **Phishing Domains:** Not used (worm propagation)
- **Exploit Servers:** Not used (direct exploitation)
- **File Hosting:** Not applicable

### Operational Infrastructure
- **VPN/Proxy:** Tor for payment sites
- **Staging Servers:** Compromised systems used as scanners
- **Data Exfiltration:** None

## Malware & Tools Used
| Tool/Malware | Type | Role in Campaign | Link |
|--------------|------|------------------|------|
| WannaCry | Ransomware/Worm | Primary payload | [[CTI/Malware/WannaCry]] |
| ETERNALBLUE | Exploit | SMBv1 RCE (CVE-2017-0144) | [[CTI/Tools/ETERNALBLUE]] |
| DOUBLEPULSAR | Backdoor/Implant | Pre-deployed backdoor for exploit | [[CTI/Tools/DOUBLEPULSAR]] |
| Mimikatz | Credential Theft | Not used in worm propagation | [[CTI/Tools/Mimikatz]] |

## IOCs Summary
> **Full IOC List:** [[CTI/IOCs/WannaCry IOCs]]

| Type | Count | Examples |
|------|-------|----------|
| File Hashes | 20+ | WannaCry variants, droppers, decryptor |
| IP Addresses | 5+ | Hardcoded C2 IPs |
| Domains | 10+ | Kill switch domains, payment domains |
| URLs | 15+ | C2 endpoints, payment URLs |
| Email Addresses | 0 | N/A |

## Timeline
| Date | Event | Description | Source |
|------|-------|-------------|--------|
| 2017-04-14 | Shadow Brokers Release | ETERNALBLUE/DOUBLEPULSAR leaked by Shadow Brokers | Shadow Brokers |
| 2017-03-14 | MS17-010 Patch | Microsoft releases patch for CVE-2017-0144 | Microsoft |
| 2017-05-12 07:00 UTC | Outbreak Begins | First infections reported (Spain, UK) | Multiple |
| 2017-05-12 15:00 UTC | Kill Switch Found | @MalwareTechBlog registers kill switch domain | MalwareTech |
| 2017-05-13 | Variant 2 | New variant without kill switch appears | Multiple |
| 2017-05-13 | Kill Switch 2 | Second kill switch registered | Multiple |
| 2017-05-15 | Outbreak Ends | Propagation largely stopped | Multiple |
| 2017-12-18 | US Attribution | White House attributes to North Korea | US Government |
| 2018-09-06 | DOJ Indictment | Park Jin-hyok charged (Lazarus) | US DOJ |

## Attribution Analysis
- **Attribution Confidence:** High
- **Key Evidence:**
  - Code overlaps with Lazarus malware (Contopee, Volgmer)
  - Same encryption routines, compilation timestamps
  - Infrastructure overlap with Lazarus campaigns
  - US DOJ indictment of Park Jin-hyok (2018)
  - UK NCSC, US NSA, NZ GCSB concurrence
- **Alternative Hypotheses:** False flag (ruled out by depth of overlaps)

## Impact Assessment
- **Organizations Compromised:** 200,000+ computers, 150+ countries
- **Data Stolen:** None (pure ransomware, no exfiltration)
- **Financial Impact:** $4-8 billion estimated global cost (downtime, recovery, ransom)
- **Operational Impact:** NHS cancelled 19,000 appointments; global disruption; wake-up call for patching

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| US DOJ | Indictment | 2018-09-06 | A | https://www.justice.gov/opa/pr/north-korean-hacker-charged |
| UK NCSC | Assessment | 2017-10 | A | https://www.ncsc.gov.uk/news/uk-response-wannacry |
| Microsoft | Blog | 2017-05 to 2018 | A | https://www.microsoft.com/security/blog/ |
| Kaspersky | Reports | 2017-2024 | A | https://securelist.com/wannacry/ |
| MalwareTech | Blog | 2017-05 | A | https://www.malwaretech.com/2017/05/ |
| MITRE ATT&CK | Campaign | 2024 | A | https://attack.mitre.org/campaigns/C0026/ |

## Related Campaigns
- [[CTI/Campaigns/NotPetya 2017]] (follow-up, same exploit chain)
- [[CTI/Campaigns/Lazarus FASTCash ATM Campaign 2017-2024]]
- [[CTI/Campaigns/Lazarus Cryptocurrency Exchange Heists 2017-2024]]

## Notes & Analysis
WannaCry was a watershed moment:
- **First global ransomware worm** using nation-state exploit (ETERNALBLUE)
- **Kill switch** accidentally stopped global propagation (Marcus Hutchins)
- **Attribution to North Korea** confirmed by US/UK governments
- **Patch management failure** exposed globally (MS17-010 patched 2 months prior)
- **Shadow Brokers leak** demonstrated danger of stockpiled exploits

The worm component (ETERNALBLUE scanner) was separate from ransomware module - suggests modular development. Ransom collection was poorly implemented (manual key assignment, no automation), suggesting either:
1. Primary goal was disruption/destruction (wiper disguised as ransomware)
2. Operators were inexperienced with ransomware operations
3. Revenue was secondary to operational objectives

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*