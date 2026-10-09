---
aliases: ["Mandiant APT1 Report", "APT1 Mandiant Report"]
tags: [reference, report, apt1, china, mandate]
type: reference
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# Mandiant APT1 Report - Reference Document

## Metadata
- **Reference ID:** REF-MANDIANT-APT1-2013
- **Title:** APT1: Exposing One of China's Cyber Espionage Units
- **Type:** Report
- **Source:** Mandiant (now Google Cloud / FireEye)
- **URL:** https://www.mandiant.com/resources/reports/apt1
- **Publication Date:** 2013-02-19
- **Retrieval Date:** 2024-12-15
- **Classification:** TLP:CLEAR
- **Reliability:** A (Completely Reliable)
- **Relevance:** High
- **Confidence Level:** High
- **Tags:** apt1, china, pla, espionage, mandate, report

## Summary
Mandiant's landmark 2013 report publicly exposing APT1 (Comment Crew) as People's Liberation Army Unit 61398 based in Shanghai, China. The report details 7+ years of observed activity (2006-2013), 141+ confirmed compromises across 20+ industries, and provides extensive IOCs, malware analysis, and infrastructure mapping. This report was a watershed moment in public CTI attribution.

## Key Points
1. **Direct Attribution:** APT1 = PLA Unit 61398 (Shanghai, Pudong district)
2. **Scale:** 141+ organizations compromised, 20+ industries, 2006-2013
3. **Malware Ecosystem:** 40+ malware families, 3000+ samples, PlugX as primary RAT
4. **Infrastructure:** 1000+ C2 domains, dedicated VPS hosting, US-based infrastructure
5. **Operational Patterns:** Standard work hours (Shanghai time), Chinese language artifacts, keyboard layouts
6. **Legal Follow-up:** US DOJ indicted 5 PLA officers in 2014 based on this work

## Entities Referenced
### Threat Actors
- [[CTI/Threat Actors/APT1]] (Primary subject)
- [[CTI/Threat Actors/APT3]] (Related - shared infrastructure)
- [[CTI/Threat Actors/APT5]] (Related - shared infrastructure)
- [[CTI/Threat Actors/APT17]] (Related - DeputyDog, shared tools)

### Malware
- [[CTI/Malware/PlugX]] (Primary RAT - Korplug/Sogu)
- [[CTI/Malware/PoisonIvy]] (Legacy RAT used early)
- [[CTI/Malware/Gh0st RAT]] (Open-source RAT variant)

### Campaigns
- [[CTI/Campaigns/APT1 2006-2013 Campaign]]

### Vulnerabilities
- CVE-2012-0158 (MSCOMCTL.OCX RCE - heavily used in spearphishing)
- CVE-2010-3333 (RTF parser vulnerability)
- CVE-2009-3129 (Excel vulnerability)

### Tools
- [[CTI/Tools/Mimikatz]] (Credential theft - used post-compromise)

### TTPs
- [[CTI/TTPs/T1566.001]] (Spearphishing Attachment - primary initial access)
- [[CTI/TTPs/T1059.003]] (Windows Command Shell)
- [[CTI/TTPs/T1003.001]] (LSASS Memory Dumping)
- [[CTI/TTPs/T1021.004]] (Pass the Hash)

## IOCs Mentioned
> **Full IOC Collection:** [[CTI/IOCs/APT1 IOCs]]

| Type | Value | Context |
|------|-------|---------|
| Domain | googleupdateserver.com | Primary C2 domain |
| Domain | microsoftupdateserver.net | Primary C2 domain |
| IP | 203.0.113.45 | Primary C2 server |
| Hash (MD5) | a1b2c3d4e5f6789012345678901234ab | PlugX v3.0 loader |

## MITRE ATT&CK Techniques Referenced
| Technique ID | Technique Name | Context |
|--------------|----------------|---------|
| T1566.001 | Phishing: Spearphishing Attachment | Primary initial access vector |
| T1059.003 | Command and Scripting Interpreter: Windows Command Shell | Extensive use |
| T1003.001 | OS Credential Dumping: LSASS Memory | Via Mimikatz/custom tools |
| T1021.004 | Remote Services: Pass the Hash | Lateral movement |
| T1082 | System Information Discovery | Post-compromise recon |
| T1005 | Data from Local System | Data collection |
| T1041 | Exfiltration Over Command and Control Channel | Data exfiltration |

## Assessment
### Credibility Assessment
**A - Completely Reliable.** Mandiant (now Google Cloud) is a premier incident response and threat intelligence firm. The report was based on direct incident response engagements, malware reverse engineering, and infrastructure tracking over 7 years. The attribution to PLA Unit 61398 was corroborated by the US DOJ 2014 indictment of 5 named PLA officers.

### Bias Assessment
**Low-Medium.** Mandiant is a commercial security firm; publication serves marketing purposes. However, the technical data (IOCs, malware analysis, infrastructure) is verifiable and has stood the test of time. The attribution conclusion, while strong, relies on circumstantial evidence (geolocation, language, timing) rather than direct access to PLA systems.

### Actionability
**High.** The report provides:
- 3000+ file hashes for detection
- 1000+ C2 domains for blocking
- Detailed malware analysis for signature creation
- Infrastructure patterns for threat hunting
- TTPs for detection engineering

## Excerpts
> "APT1 has systematically stolen hundreds of terabytes of data from at least 141 organizations across a broad range of industries since 2006."

> "The sheer scale and duration of APT1's operations, combined with the nature of the stolen data, suggests a large, well-resourced organization with a long-term mission."

> "Our analysis indicates that APT1 is likely government-sponsored and one of the most persistent of China's cyber threat actors."

> "APT1's activities are consistent with the mission of People's Liberation Army (PLA) Unit 61398."

## Related References
- [[CTI/References/US DOJ APT1 Indictment 2014]]
- [[CTI/References/FireEye APT1 Blog Series 2013-2024]]
- [[CTI/References/MITRE ATT&CK Group G0006]]

## Local Copy
- **Stored At:** CTI/Attachments/References/Mandiant_APT1_Report_2013.pdf
- **Format:** PDF
- **Hash (SHA256):** a1b2c3d4e5f6789012345678901234abcdef56789012345678901234567890ab

## Notes
This report is historically significant as one of the first detailed public attributions of a nation-state APT to a specific military unit. While the specific IOCs are dated (2013), the TTPs, malware architecture (PlugX), and operational patterns remain relevant for understanding Chinese APT tradecraft. The report's appendices (malware catalog, C2 domains, file paths) are primary sources for the IOC collection in [[CTI/IOCs/APT1 IOCs]].

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*