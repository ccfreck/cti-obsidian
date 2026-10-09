---
aliases: ["Hidden Cobra", "Guardians of Peace", "Lazarus Group", "APT38", "Bluenoroff", "Andariel", "Diamond Sleet"]
tags: [threat-actor, apt, north-korea, cybercrime]
type: APT
actor_type: APT
origin: North Korea
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
campaigns:
  - "[[CTI/Campaigns/WannaCry Ransomware 2017]]"
  - "[[CTI/Campaigns/Operation Troy 2009-2012]]"
  - "[[CTI/Campaigns/Sony Pictures Hack 2014]]"
  - "[[CTI/Campaigns/Bangladesh Bank Heist 2016]]"
malware:
  - "[[CTI/Malware/WannaCry]]"
  - "[[CTI/Malware/Dtrack]]"
  - "[[CTI/Malware/Cobalt Strike]]"
tools:
  - "[[CTI/Tools/Mimikatz]]"
---

# Lazarus Group - Threat Actor Profile

## Overview
- **Name:** Lazarus Group
- **Aliases:** Hidden Cobra, Guardians of Peace, APT38, Bluenoroff, Andariel, Diamond Sleet
- **Type:** APT / Cybercrime (state-sponsored)
- **Origin/Country:** North Korea (Reconnaissance General Bureau - RGB)
- **First Observed:** 2009
- **Last Activity:** 2024
- **Status:** active
- **Confidence Level:** high

## Description
Lazarus Group is a North Korean state-sponsored threat actor responsible for some of the most destructive and financially damaging cyber operations in history. They conduct both espionage and financially motivated attacks (bank heists, cryptocurrency theft, ransomware) to generate revenue for the regime. Sub-groups include Bluenoroff (financial), Andariel (espionage), and APT38 (financial).

## Goals & Motivation
- **Primary Goal:** Revenue generation for regime (sanctions evasion)
- **Secondary Goals:** Espionage, destructive attacks, political retaliation
- **Motivation:** State survival, sanctions evasion, intelligence collection

## Targeting
### Sectors Targeted
- **Financial:** Banks, SWIFT infrastructure, ATMs, Cryptocurrency Exchanges, DeFi
- **Espionage:** Defense, Aerospace, Government, Think Tanks, Media, Cryptocurrency
- **Destructive:** Entertainment (Sony Pictures), Critical Infrastructure

### Geographic Targeting
- Global: South Korea, United States, Japan, Europe, Southeast Asia, Latin America, Africa, Middle East

### Notable Victims
- Sony Pictures (2014), Bangladesh Bank (2016 - $81M), WannaCry (2017), FASTCash ATM attacks, Cryptocurrency exchanges ($3B+ stolen), Ronin Bridge (2022 - $625M), Harmony Bridge (2022 - $100M), Atomic Wallet (2023 - $100M+)

## Capabilities & Resources
- **Sophistication Level:** advanced
- **Funding Source:** North Korean regime (RGB)
- **Team Size:** Large, organized in sub-units
- **Infrastructure:** Global proxy networks, compromised infrastructure, VPS, VPNs

## TTPs (MITRE ATT&CK Mapping)
| Technique ID | Technique Name | Description | Sub-techniques |
|--------------|----------------|-------------|----------------|
| T1566.001 | Phishing: Spearphishing Attachment | Job lure phishing (fake recruiter docs) | .001, .002 |
| T1566.002 | Phishing: Spearphishing Link | Credential harvesting | |
| T1190 | Exploit Public-Facing Application | Log4j, ProxyLogon, ZeroLogon, etc. | |
| T1203 | Exploitation for Client Execution | Browser exploits, document exploits | |
| T1059.001 | PowerShell | | |
| T1059.003 | Windows Command Shell | | |
| T1059.005 | Visual Basic | VBScript/VBA macros | |
| T1027.002 | Obfuscated Files: Software Packing | Custom packers, VMProtect, Themida | |
| T1055.012 | Process Injection: Process Hollowing | | |
| T1574.001 | DLL Search Order Hijacking | DLL sideloading extensively | .001, .002 |
| T1003.001 | OS Credential Dumping: LSASS Memory | | |
| T1550.002 | Pass the Hash | | |
| T1486 | Data Encrypted for Impact | Ransomware (WannaCry, VHD Ransomware) | |
| T1490 | Inhibit System Recovery | Wiper malware (Shamoon-style) | |
| T1573.001 | Encrypted Channel: Symmetric Cryptography | Custom C2 encryption | |
| T1090.003 | Proxy: Multi-hop Proxy | Extensive proxy chains | |
| T1583.005 | Acquire Infrastructure: Botnet | Compromised device networks | |

> **Related TTPs:** [[CTI/TTPs/]]

## Malware & Tools Used
| Malware/Tool | Type | Description | Links |
|--------------|------|-------------|-------|
| Dtrack | RAT/Backdoor | Multi-platform, used in financial/espionage | [[CTI/Malware/Dtrack]] |
| Manuscrypt | Backdoor | Used in bank heists | |
| Nestegg | Backdoor | Lightweight implant | |
| VHD Ransomware | Ransomware | Custom ransomware | |
| WannaCry | Ransomware/Wiper | Global ransomware/wiper | [[CTI/Malware/WannaCry]] |
| FASTCash | ATM Malware | ATM cash-out malware | |
| BlindingCan | Backdoor | macOS targeting | |
| RustBucket | Backdoor | macOS, Rust-based | |
| KANDYKORN | Backdoor | macOS, Discord C2 | |
| Mimikatz | Credential Theft | | [[CTI/Tools/Mimikatz]] |
| Custom Loaders | Loader | Numerous custom loaders/droppers | |

> **See also:** [[CTI/Malware/]], [[CTI/Tools/]]

## Infrastructure & IOCs
### Command & Control
- **C2 Domains:** Dynamic DNS, compromised domains, blockchain domains (.bit, .eth)
- **C2 IPs:** Compromised servers globally, VPS, Tor
- **Protocols:** HTTP/HTTPS, custom binary, Discord/Telegram APIs, blockchain

### Host-Based IOCs
- **File Hashes:** 1000+ samples across families
- **Registry Keys:** Run keys, services, WMI
- **Mutexes:** Family-specific (e.g., `Global\DtrackMutex`)
- **File Paths:** `%APPDATA%\`, `%TEMP%\`, `%PROGRAMDATA%\`

### Network IOCs
- **IP Addresses:** Global proxy network
- **Domains:** Typosquatting, dynamic DNS, blockchain
- **URLs:** Job recruitment sites, fake company sites

> **Full IOC List:** [[CTI/IOCs/Lazarus Group IOCs]]

## Associated Campaigns
- [[CTI/Campaigns/Operation Troy 2009-2012]]
- [[CTI/Campaigns/Sony Pictures Hack 2014]]
- [[CTI/Campaigns/Bangladesh Bank Heist 2016]]
- [[CTI/Campaigns/WannaCry 2017]]
- [[CTI/Campaigns/FASTCash ATM Campaign 2017-2024]]
- [[CTI/Campaigns/Cryptocurrency Exchange Heists 2017-2024]]
- [[CTI/Campaigns/DeFi Bridge Exploits 2022-2024]]
- [[CTI/Campaigns/Job Lure Phishing Campaigns 2020-2024]]

## Attribution & Relationships
- **Attributed To:** North Korea RGB (Bureau 121) - US DOJ, US Treasury, UN Panel of Experts
- **Sub-groups:** Bluenoroff (APT38 - financial), Andariel (espionage), Diamond Sleet (espionage)
- **Related Actors:** Kimsuky (APT43) - separate but occasionally overlapping infrastructure
- **Collaborations:** Shares some tooling with other NK groups

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| US DOJ | Indictments | 2018-2024 | A | https://www.justice.gov/opa/pr/north-korean-hackers-charged |
| US Treasury | Advisory | 2019-2024 | A | https://home.treasury.gov/policy-issues/financial-sanctions |
| UN Panel of Experts | Report | 2019-2024 | A | https://www.un.org/securitycouncil/sanctions/1718/panel-experts |
| Kaspersky | Reports | 2013-2024 | A | https://securelist.com/ |
| MITRE ATT&CK | Framework | 2024 | A | https://attack.mitre.org/groups/G0032/ |

## Notes & Analysis
Lazarus is the most financially destructive APT group in history, with estimated $3B+ in cryptocurrency theft alone. Their evolution shows increasing sophistication in blockchain/DeFi targeting. The group operates with distinct sub-units but shares core tooling (loaders, encryption, C2 frameworks).

Key characteristics:
- **Financial focus:** Unique among APTs for scale of financial crime
- **Blockchain expertise:** Advanced DeFi/smart contract exploitation
- **Job lure phishing:** Highly effective social engineering (fake LinkedIn recruiters)
- **Wiper capability:** Willing to destroy data (Sony, WannaCry)
- **Sanctions evasion:** Crypto mixing, chain hopping, DeFi laundering

The Bluenoroff/APT38 sub-unit specializes in SWIFT/banking attacks; Andariel focuses on South Korean targets and espionage.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*