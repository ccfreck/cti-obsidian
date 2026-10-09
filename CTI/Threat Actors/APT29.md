---
aliases: ["Cozy Bear", "The Dukes", "NOBELIUM", "YTTRIUM", "UNC2452", "Dark Halo", "StellarParticle"]
tags: [threat-actor, apt, russia, svr, nation-state]
type: threat-actor
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# APT29 - Threat Actor Profile

## Overview
- **Name:** APT29
- **Aliases:** Cozy Bear, The Dukes, NOBELIUM, YTTRIUM, UNC2452, Dark Halo, StellarParticle
- **Type:** APT (Advanced Persistent Threat), Nation-State
- **Origin/Country:** Russia (attributed to SVR - Foreign Intelligence Service)
- **First Observed:** 2008
- **Last Activity:** 2024 (ongoing)
- **Status:** active
- **Confidence Level:** high

## Description
APT29 (Cozy Bear/The Dukes) is a sophisticated Russian nation-state threat actor attributed to the SVR (Foreign Intelligence Service). Active since at least 2008, they conduct long-term espionage campaigns targeting governments, think tanks, healthcare, energy, and technology sectors globally. Known for advanced tradecraft, supply chain compromises, and cloud identity attacks.

## Goals & Motivation
- **Primary Goal:** Strategic intelligence collection (political, diplomatic, military, technological)
- **Secondary Goals:** Access to privileged networks, pre-positioning for future operations, influence operations support
- **Motivation:** State espionage on behalf of Russian Federation

## Targeting
### Sectors Targeted
- Government (foreign ministries, defense, intelligence)
- Think Tanks & Policy Institutes
- Healthcare & Pharmaceutical (COVID-19 research)
- Technology & Telecommunications
- Energy & Critical Infrastructure
- Education & Research
- Diplomatic Missions & NGOs

### Geographic Targeting
- Primary: NATO member states, United States, Europe
- Secondary: Former Soviet states, Asia-Pacific, Global organizations
- Notable: Heavy focus on US and European governments

### Notable Victims
- US Government (State Dept, White House, Pentagon - 2014-2015)
- Democratic National Committee (2016)
- Norwegian Parliament (2020)
- SolarWinds Supply Chain (~18,000 orgs, 2020)
- COVID-19 Vaccine Research Orgs (2020-2021)
- Microsoft, Mimecast, other tech providers (2021)

## Capabilities & Resources
- **Sophistication Level:** Advanced (top-tier nation-state)
- **Funding Source:** State-sponsored (SVR budget)
- **Team Size:** Large, organized into specialized cells
- **Infrastructure:** Extensive, includes compromised legitimate infrastructure, dedicated VPS, domain fronting, cloud services

## TTPs (MITRE ATT&CK Mapping)
| Technique ID | Technique Name | Description | Sub-techniques |
|--------------|----------------|-------------|----------------|
| T1195.002 | Supply Chain Compromise: Software | SolarWinds Orion build compromise | SUNBURST injection |
| T1190 | Exploit Public-Facing Application | Zimbra, Exchange, VMware exploits | CVE-2022-22954, CVE-2021-26855 |
| T1078 | Valid Accounts | Cloud/SAML token theft, credential reuse | T1078.004 (Cloud) |
| T1558.003 | Kerberoasting | Service account credential theft | Rubeus |
| T1003.006 | DCSync | Domain controller replication | Mimikatz |
| T1550.003 | Pass the Ticket | Kerberos delegation abuse | Rubeus |
| T1556.002 | Password Filter | Custom password filter on AD DCs | SUNBURST/TEARDROP |
| T1021.004 | Pass the Hash | Lateral movement | Cobalt Strike |
| T1505.003 | Web Shell | Persistence on web servers | Custom, China Chopper |
| T1574.002 | DLL Side-Loading | SUNBURST via SolarWinds.BusinessLayerHost | SUNBURST |
| T1573.001 | Encrypted Channel: Symmetric | SUNBURST custom crypto, Cobalt Strike | SUNBURST, CS |
| T1041 | Exfiltration Over C2 Channel | Data theft via C2 | SUNBURST, TEARDROP |
| T1608.001 | Stage Capabilities: Upload Malware | Tool staging | TEARDROP/RAINDROP |

> **Related TTPs:** [[CTI/TTPs/]]

## Malware & Tools Used
| Malware/Tool | Type | Description | Links |
|--------------|------|-------------|-------|
| SUNBURST | Backdoor | Primary supply chain implant | [[CTI/Malware/SUNBURST]] |
| TEARDROP | Loader | Memory-only Cobalt Strike loader | [[CTI/Malware/TEARDROP]] |
| RAINDROP | Loader | Second-stage loader | [[CTI/Malware/RAINDROP]] |
| Cobalt Strike | C2 Framework | Post-exploitation | [[CTI/Tools/Cobalt Strike]] |
| Mimikatz | Credential Theft | LSASS dumping, DCSync | [[CTI/Tools/Mimikatz]] |
| Rubeus | Kerberos Abuse | Ticket operations, delegation | [[CTI/Tools/Rubeus]] |
| WellMess | Backdoor | Custom Go backdoor | [[CTI/Malware/WellMess]] |
| GoldMax | Backdoor | Custom Go backdoor (Linux) | [[CTI/Malware/GoldMax]] |
| GoldFinder | Network Scanner | Network mapping | Custom |
| Sibot | Persistence | Scheduled task persistence | Custom |
| FoggyWeb | Backdoor | AD FS compromise | Custom |
| MagicWeb | Backdoor | AD FS SAML token manipulation | Custom |
| ADFind | Recon | AD enumeration | [[CTI/Tools/ADFind]] |
| PowerShell | Scripting | Extensive automation | [[CTI/Tools/PowerShell]] |

> **See also:** [[CTI/Malware/]], [[CTI/Tools/]]

## Infrastructure & IOCs
### Command & Control
- **C2 Domains:** `avsvmcloud.com`, `deftsecurity.com`, `freescanonline.com`, `thedoccloud.com`, `highdatabase.com`, `incomeupdate.com`, `databasegalore.com`, `zupertech.com`, `virtualdataserver.com`, `webtags.org` (SUNBURST); Dynamic/Compromised for Cobalt Strike
- **C2 IPs:** Hosted on major cloud providers (AWS, Azure, DigitalOcean, Azure), dedicated VPS, compromised infrastructure
- **Protocols:** HTTPS (SUNBURST), HTTP/DNS/SMB (Cobalt Strike), Custom encryption
- **Domain Fronting:** Azure, CloudFront, Akamai CDNs

### Host-Based IOCs
- **File Hashes:** SUNBURST (multiple versions), TEARDROP, RAINDROP, Cobalt Strike Beacons, WellMess, GoldMax, GoldFinder, Sibot, FoggyWeb, MagicWeb
- **Registry Keys:** `HKLM\SOFTWARE\SolarWinds\Orion\Core\BusinessLayerHost` (SUNBURST), Custom C2 keys
- **Mutexes:** SUNBURST-specific, Cobalt Strike `Global\Beacon_Mutex_*`
- **File Paths:** `%PROGRAMFILES%\SolarWinds\Orion\SolarWinds.BusinessLayerHost.dll` (SUNBURST), `%TEMP%\beacon_*.tmp`

### Network IOCs
- **IP Addresses:** 100+ C2/redirector IPs (varies per campaign)
- **Domains:** 20+ C2 domains (SUNBURST), dynamic for other ops
- **URLs:** `/api/v1/...`, `/jquery/`, `/analytics/` (malleable C2)

> **Full IOC List:** [[CTI/IOCs/APT29 IOCs]]

## Associated Campaigns
- [[CTI/Campaigns/SolarWinds Supply Chain Attack]]
- [[CTI/Campaigns/APT29 COVID-19 Research Targeting 2020]]
- [[CTI/Campaigns/APT29 2021-2024 Campaigns]]
- [[CTI/Campaigns/APT29 DNC 2016]]
- [[CTI/Campaigns/APT29 US Govt 2014-2015]]

## Attribution & Relationships
- **Attributed To:** Russian SVR (Foreign Intelligence Service) - High Confidence (US IC, UK NCSC, NATO)
- **Related Actors:** APT28 (Fancy Bear/GRU) - different agency, occasional overlap; Turla (FSB) - distinct but occasional infrastructure sharing
- **Collaborations:** No direct evidence of operational collaboration with other Russian APTs

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| Microsoft | Blog/Report | 2020-2024 | A | https://www.microsoft.com/security/blog/ |
| Mandiant/FireEye | Report | 2020-2024 | A | https://www.mandiant.com/resources |
| UK NCSC | Advisory | 2021 | A | https://www.ncsc.gov.uk/ |
| US CISA | Alert | 2020-2024 | A | https://www.cisa.gov/ |
| MITRE ATT&CK | Group | 2024 | A | https://attack.mitre.org/groups/G0016/ |
| CrowdStrike | Report | 2020-2024 | A | https://www.crowdstrike.com/ |
| Volexity | Blog | 2021 | A | https://www.volexity.com/blog/ |
| Kaspersky | Report | 2021 | A | https://securelist.com/ |

## Notes & Analysis
APT29 represents one of the most sophisticated and persistent nation-state actors globally. Key characteristics:

1. **Supply Chain Mastery:** SolarWinds (SUNBURST) represents the gold standard of software supply chain compromise
2. **Cloud Identity Expertise:** Pioneered Golden SAML, Azure AD token forgery, cloud-to-on-prem pivot
3. **Operational Security:** Exceptional compartmentalization, custom tooling per target, minimal reuse
4. **Long-Term Access:** Campaigns span years; maintain access even after detection
5. **Adaptability:** Rapidly adopt new techniques (MFA bypass, cloud attacks, zero-days)

The SVR attribution is among the highest-confidence in public intelligence, supported by multiple Western intelligence agencies.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*