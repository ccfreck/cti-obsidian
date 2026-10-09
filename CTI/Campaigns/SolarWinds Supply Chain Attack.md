---
aliases: ["SolarWinds Hack", "SUNBURST", "Solorigate", "NOBELIUM Campaign"]
tags: [campaign, apt, russia, supply-chain]
type: campaign
status: completed
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
threat_actors:
  - "[[CTI/Threat Actors/APT28]]"
malware:
  - "[[CTI/Malware/SUNBURST]]"
  - "[[CTI/Malware/TEARDROP]]"
  - "[[CTI/Malware/RAINDROP]]"
  - "[[CTI/Malware/Cobalt Strike]]"
tools:
  - "[[CTI/Tools/Mimikatz]]"
  - "[[CTI/Tools/Rubeus]]"
start_date: "2019-09-01"
end_date: "2020-12-13"
---

# SolarWinds Supply Chain Attack - Campaign Profile

## Overview
- **Name:** SolarWinds Supply Chain Attack
- **Aliases:** SUNBURST, Solorigate, NOBELIUM Campaign
- **Threat Actor(s):** [[CTI/Threat Actors/APT29]] (Cozy Bear, The Dukes, NOBELIUM)
- **Start Date:** 2019-09 (build compromise)
- **End Date:** 2020-12 (discovery)
- **Status:** completed
- **Confidence Level:** high

## Description
The SolarWinds supply chain attack (SUNBURST) was a sophisticated software supply chain compromise targeting SolarWinds Orion platform build system. The attackers injected malicious code (SUNBURST backdoor) into legitimate Orion software updates, which were then distributed to ~18,000 customers. This represents one of the most significant supply chain attacks in history, affecting US government agencies, Fortune 500 companies, and critical infrastructure globally.

## Objectives
- **Primary Objective:** Long-term persistent access to high-value targets (government, tech, telecom)
- **Secondary Objectives:** Intelligence collection, credential theft, lateral movement to cloud environments

## Targeting
### Victims
| Victim | Sector | Country | Compromise Date | Impact |
|--------|--------|---------|-----------------|--------|
| US Treasury | Government | USA | 2020-03 | Email access, data theft |
| US Commerce (NTIA) | Government | USA | 2020-03 | Email access |
| US State Dept | Government | USA | 2020-03 | Email access |
| US DHS | Government | USA | 2020-03 | Limited access |
| FireEye | Cybersecurity | USA | 2020-03 | Red team tools stolen |
| Microsoft | Technology | USA | 2020-03 | Source code access |
| Cisco | Technology | USA | 2020-03 | Limited access |
| Intel | Technology | USA | 2020-03 | Limited access |
| Nvidia | Technology | USA | 2020-03 | Limited access |
| VMware | Technology | USA | 2020-03 | Limited access |
| Belkin | Consumer Electronics | USA | 2020-03 | Limited access |
| + 18,000 Orion customers | Various | Global | 2020-03 to 2020-12 | Varied |

### Geographic Scope
- Primary: United States (government, critical infrastructure)
- Secondary: NATO allies, global tech companies
- ~100 organizations selected for hands-on-keyboard activity

### Sector Focus
- Government (US Federal), Technology, Telecommunications, Cybersecurity, Consulting, Energy, Aerospace

## Attack Chain (MITRE ATT&CK)
| Phase | Technique ID | Technique Name | Description | Tools/Malware |
|-------|--------------|----------------|-------------|---------------|
| Initial Access | T1195.002 | Supply Chain Compromise: Software Supply Chain | Compromised SolarWinds build system, injected SUNBURST into Orion updates | SUNBURST |
| Execution | T1059.001 | Command and Scripting Interpreter: PowerShell | SUNBURST executes PowerShell for reconnaissance | SUNBURST, PowerShell |
| Persistence | T1505.003 | Server Software Component: Web Shell | TEARDROP/RAINDROP loaders, custom webshells | TEARDROP, RAINDROP |
| Persistence | T1556.002 | Credential Theft: Password Filter | Custom password filter on AD | Custom |
| Privilege Escalation | T1068 | Exploitation for Privilege Escalation | CVE-2020-1472 (ZeroLogon) | ZeroLogon exploit |
| Defense Evasion | T1574.002 | Hijack Execution Flow: DLL Side-Loading | SUNBURST DLL sideloading via SolarWinds.BusinessLayerHost.exe | SUNBURST |
| Defense Evasion | T1070.004 | Indicator Removal: File Deletion | Log cleaning, artifact removal | SUNBURST, custom tools |
| Credential Access | T1003.001 | OS Credential Dumping: LSASS Memory | Mimikatz, built-in Beacon commands | Mimikatz, Cobalt Strike |
| Credential Access | T1558.003 | Kerberoasting | Service account credential theft | Rubeus |
| Discovery | T1082 | System Information Discovery | Extensive AD/enumeration | SUNBURST, Cobalt Strike, PowerShell |
| Discovery | T1069.002 | Permission Groups Discovery: Domain Groups | AD group enumeration | PowerShell, BloodHound |
| Lateral Movement | T1021.004 | Remote Services: Pass the Hash | Lateral movement using stolen credentials | Cobalt Strike |
| Lateral Movement | T1550.003 | Use Alternate Authentication Material: Pass the Ticket | Kerberos delegation abuse | Rubeus |
| Collection | T1005 | Data from Local System | Email, documents, source code collection | SUNBURST, Cobalt Strike |
| Collection | T1530 | Data from Cloud Storage | Azure/Office 365 data access | Azure AD Graph API, PowerShell |
| Exfiltration | T1041 | Exfiltration Over Command and Control Channel | Data exfil via SUNBURST/C2 channels | SUNBURST, TEARDROP |
| Command & Control | T1573.001 | Encrypted Channel: Symmetric Cryptography | SUNBURST custom encryption, Cobalt Strike Malleable C2 | SUNBURST, Cobalt Strike |

## Infrastructure
### Command & Control
- **Domains:** `avsvmcloud.com`, `deftsecurity.com`, `freescanonline.com`, `thedoccloud.com`, `highdatabase.com`, `incomeupdate.com`, `databasegalore.com`, `zupertech.com`, `virtualdataserver.com`, `webtags.org`
- **IPs:** Hosted on US cloud providers (AWS, Azure, DigitalOcean), dedicated VPS
- **Protocols:** HTTPS (SUNBURST), HTTP/DNS (Cobalt Strike), custom encryption

### Delivery Infrastructure
- **Phishing Domains:** Not primary vector (supply chain)
- **Exploit Servers:** SolarWinds build server (compromised)
- **File Hosting:** SolarWinds CDN (legitimate update distribution)

### Operational Infrastructure
- **VPN/Proxy:** Compromised infrastructure, dedicated VPS
- **Staging Servers:** Compromised victim systems used as jump hosts
- **Data Exfiltration:** Direct C2, cloud storage APIs

## Malware & Tools Used
| Tool/Malware | Type | Role in Campaign | Link |
|--------------|------|------------------|------|
| SUNBURST | Backdoor | Primary implant via Orion update | [[CTI/Malware/SUNBURST]] |
| TEARDROP | Loader | Memory-only loader for Cobalt Strike | [[CTI/Malware/TEARDROP]] |
| RAINDROP | Loader | Second-stage loader | [[CTI/Malware/RAINDROP]] |
| Cobalt Strike | C2 Framework | Post-exploitation, lateral movement | [[CTI/Tools/Cobalt Strike]] |
| Mimikatz | Credential Theft | Credential dumping | [[CTI/Tools/Mimikatz]] |
| Rubeus | Kerberos Abuse | Kerberoasting, delegation | [[CTI/Tools/Rubeus]] |
| ADFind | Recon | Active Directory enumeration | [[CTI/Tools/ADFind]] |
| PowerShell | Scripting | Extensive use for automation | [[CTI/Tools/PowerShell]] |
| Custom Password Filter | Credential Theft | Persistent credential capture | Custom |

## IOCs Summary
> **Full IOC List:** [[CTI/IOCs/SolarWinds IOCs]]

| Type | Count | Examples |
|------|-------|----------|
| File Hashes | 50+ | SUNBURST (multiple versions), TEARDROP, RAINDROP, Cobalt Strike Beacons |
| IP Addresses | 100+ | C2 IPs, redirectors |
| Domains | 20+ | C2 domains, DGA domains |
| URLs | 30+ | C2 endpoints |
| Email Addresses | 10+ | Phishing (limited use) |

## Timeline
| Date | Event | Description | Source |
|------|-------|-------------|--------|
| 2019-09 | Build Compromise | Attackers gain access to SolarWinds build environment | Microsoft, SolarWinds |
| 2020-02 | SUNBURST Compilation | First malicious Orion build compiled | Microsoft |
| 2020-03 | Orion Update Release | Orion 2019.4 HF5 / 2020.2.1 released with SUNBURST | SolarWinds |
| 2020-03 to 2020-12 | Customer Updates | ~18,000 customers install compromised updates | SolarWinds |
| 2020-12-08 | FireEye Discovery | FireEye detects compromise, discloses theft of red team tools | FireEye |
| 2020-12-13 | Public Disclosure | SolarWinds, FireEye, Microsoft, US CISA coordinate disclosure | Multiple |
| 2020-12-14 | Emergency Directive | CISA ED 21-01: Mitigate SolarWinds Orion Compromise | CISA |
| 2021-01 | Attribution | US IC attributes to Russian SVR (APT29) | US Government |

## Attribution Analysis
- **Attribution Confidence:** High
- **Key Evidence:** 
  - TTPs consistent with APT29 (NOBELIUM)
  - Infrastructure overlap with previous APT29 campaigns
  - Code similarities with APT29 malware (WellMess, GoldMax)
  - Operational security discipline consistent with SVR
  - US IC formal attribution (Jan 2021)
- **Alternative Hypotheses:** None credible

## Impact Assessment
- **Organizations Compromised:** ~18,000 installed updates; ~100 selected for deep compromise
- **Data Stolen:** Emails, source code, credentials, documentation, cryptographic keys
- **Financial Impact:** Billions in remediation, investigation, security improvements
- **Operational Impact:** Massive incident response across government/industry; trust in software supply chain severely damaged

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| Microsoft | Blog/Report | 2020-12 to 2021 | A | https://www.microsoft.com/security/blog/2020/12/13/ |
| FireEye/Mandiant | Blog/Report | 2020-12 to 2021 | A | https://www.fireeye.com/blog/threat-research/2020/12/ |
| SolarWinds | Advisory | 2020-12 | A | https://www.solarwinds.com/securityadvisory |
| CISA | Emergency Directive | 2020-12-14 | A | https://www.cisa.gov/emergency-directive-21-01 |
| US IC | Assessment | 2021-01 | A | https://www.dni.gov/ |
| Kaspersky | Report | 2021 | A | https://securelist.com/solarwinds/ |
| MITRE ATT&CK | Campaign | 2024 | A | https://attack.mitre.org/campaigns/C0024/ |

## Related Campaigns
- [[CTI/Campaigns/APT29 COVID-19 Research Targeting 2020]]
- [[CTI/Campaigns/APT29 2021-2024 Campaigns]]

## Notes & Analysis
The SolarWinds attack represents a paradigm shift in supply chain threats:
- **Scale:** 18,000 organizations received compromised software
- **Stealth:** Malicious code signed with valid SolarWinds certificate
- **Precision:** Only ~100 high-value targets received hands-on activity
- **Cloud pivot:** Rapid movement from on-prem AD to Azure/Office 365 (Golden SAML, Azure AD token forgery)
- **Attribution:** Rare public US IC attribution to Russian SVR (APT29)

Key lessons:
1. Software build integrity is critical (reproducible builds, signed artifacts verification)
2. Trust but verify - even signed software from trusted vendors
3. Cloud identity is the new perimeter (Golden SAML, token theft)
4. Nation-state actors will burn massive access for high-value targets

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*