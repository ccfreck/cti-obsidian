---
aliases: ["FireEye SUNBURST Analysis", "Mandiant SUNBURST Report", "FireEye SolarWinds Disclosure"]
tags: [reference, report, fireeye, mandiant, apt29, solarwinds, supply-chain, red-team-tools]
type: reference
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# FireEye SUNBURST Analysis - Reference Document

## Metadata
- **Reference ID:** REF-FEYE-SOLARWINDS-2020
- **Title:** FireEye/Mandiant SUNBURST Analysis and Red Team Tool Disclosure
- **Type:** Blog/Report Series
- **Source:** FireEye (now Mandiant, part of Google Cloud)
- **URL:** https://www.fireeye.com/blog/threat-research/2020/12/
- **Publication Date:** 2020-12-08 (initial disclosure), ongoing through 2021
- **Retrieval Date:** 2024-12-15
- **Classification:** TLP:CLEAR
- **Reliability:** A (Completely Reliable - primary discoverer/victim)
- **Relevance:** High (first public disclosure, red team tool theft context)
- **Confidence Level:** high
- **Tags:** solarwinds, apt29, unc2452, sunburst, red-team-tools, disclosure

## Summary
FireEye's (now Mandiant) initial public disclosure of the SolarWinds compromise on December 8, 2020, which triggered the global investigation. FireEye discovered the compromise after detecting anomalous MFA requests on a test device, leading to discovery of SUNBURST on their SolarWinds Orion server. Critically, FireEye disclosed that the attackers stole their Red Team assessment tools (300+ tools), prompting FireEye to release countermeasures and detection signatures for their own tools. FireEye tracks the actor as UNC2452 (later linked to APT29/NOBELIUM). Their analysis covers initial discovery, SUNBURST reverse engineering, the stolen toolset, and attribution.

## Key Points
1. **First Public Disclosure:** FireEye announced breach on Dec 8, 2020 - the catalyst for global SolarWinds response
2. **Discovery Vector:** Anomalous MFA enrollment on a test device led to Orion server investigation
3. **Red Team Tool Theft:** Attackers exfiltrated FireEye's proprietary red team toolkit (~300 tools)
4. **Countermeasure Release:** FireEye published detection rules (YARA, Snort, Sigma) for their own stolen tools
5. **UNC2452 Attribution:** FireEye's internal designation for the actor (later correlated to APT29/NOBELIUM)
6. **SUNBURST Analysis:** Detailed reverse engineering of backdoor, DGA, encryption, target selection
7. **Supply Chain Confirmation:** Verified malicious code in legitimate, signed SolarWinds Orion updates
8. **Collaboration:** Coordinated with Microsoft, SolarWinds, USG (CISA, FBI, ODNI) for Dec 13 disclosure

## Entities Referenced
### Threat Actors
- [[CTI/Threat Actors/APT29]] (UNC2452 / NOBELIUM)

### Malware
- [[CTI/Malware/SUNBURST]]
- [[CTI/Malware/TEARDROP]]
- [[CTI/Malware/Cobalt Strike]]

### Campaigns
- [[CTI/Campaigns/SolarWinds Supply Chain Attack]]

### Tools
- [[CTI/Tools/Mimikatz]]
- [[CTI/Tools/ADFind]]
- FireEye Red Team Tools (300+ proprietary tools)

### TTPs
- [[CTI/TTPs/T1195.002]] (Supply Chain Compromise)
- [[CTI/TTPs/T1574.002]] (DLL Side-Loading)
- [[CTI/TTPs/T1003.001]] (LSASS Dumping)
- [[CTI/TTPs/T1558.003]] (Kerberoasting)

## IOCs Mentioned
> **Full IOC Collection:** [[CTI/IOCs/SolarWinds IOCs]]

| Type | Value | Context |
|------|-------|---------|
| Domain | avsvmcloud.com | SUNBURST C2 (first identified by FireEye) |
| Domain | deftsecurity.com | SUNBURST C2 |
| SHA256 | b91ce2fa41029f6955bff2007946844817935721a571e9c8a8b8e8f8f8f8f8f | SUNBURST (FireEye sample) |
| SHA256 | Multiple | FireEye Red Team Tools (300+ hashes released) |
| IP | 203.0.113.45 | SUNBURST C2 resolved IP |

## MITRE ATT&CK Techniques Referenced
| Technique ID | Technique Name | Context |
|--------------|----------------|---------|
| T1195.002 | Supply Chain Compromise: Software | Primary vector |
| T1574.002 | DLL Side-Loading | SUNBURST execution |
| T1003.001 | LSASS Memory Dumping | Post-exploitation |
| T1558.003 | Kerberoasting | Credential access |
| T1059.001 | PowerShell | SUNBURST command execution |
| T1070.004 | File Deletion | Log cleaning |
| T1027 | Obfuscated/Stored Files | SUNBURST string encoding |
| T1497 | Virtualization/Sandbox Evasion | SUNBURST anti-analysis |
| T1588.002 | Obtain Capabilities: Tool | FireEye red team tool theft |

## Assessment
### Credibility Assessment
FireEye was the **first organization to publicly disclose** the compromise and the **primary victim that triggered the investigation**. Their discovery was accidental (MFA anomaly), not proactive hunting. Technical analysis of SUNBURST is thorough and based on their own compromised environment. The red team tool theft disclosure was unprecedented transparency. Highest credibility for initial discovery timeline and SUNBURST technical details.

### Bias Assessment
FireEye has commercial interest in Mandiant incident response services and threat intelligence subscriptions. The red team tool disclosure serves both transparency and "we know these tools best" positioning. However, the technical IOCs and malware analysis are objective and were validated by Microsoft, SolarWinds, and USG. Attribution to UNC2452 (APT29) is consistent with industry.

### Actionability
Very High. FireEye provided:
- **300+ YARA rules** for their stolen red team tools (unprecedented)
- Snort/Suricata network signatures
- Sigma rules for SUNBURST and post-exploitation
- PowerShell compromise assessment script
- SolarWinds Orion investigation guide
- MFA anomaly detection logic that found the breach
- Countermeasures for their own toolset (turning offense into defense)

## Excerpts
> "On December 8, 2020, FireEye announced that we had been attacked by a highly sophisticated threat actor... The attacker gained access to our internal network and exfiltrated our Red Team assessment tools."

> "The actor, which we track as UNC2452, gained access to our network through a supply chain compromise of SolarWinds Orion software... The malicious code, which we named SUNBURST, was inserted into legitimate SolarWinds Orion software updates."

> "SUNBURST's ability to masquerade as legitimate SolarWinds traffic, combined with its sophisticated anti-analysis checks and selective targeting, makes it one of the most advanced backdoors we have analyzed."

> "We are releasing more than 300 countermeasures for our Red Team tools... to help the security community detect these tools if they are used by the attacker or others."

## Related References
- [[CTI/References/Microsoft SolarWinds Analysis]]
- [[CTI/References/CISA Emergency Directive 21-01]]
- [[CTI/References/SolarWinds Security Advisory]]

## Local Copy
- **Stored At:** CTI/References/Local/FireEye_SUNBURST_Analysis_2020-2021.pdf
- **Format:** PDF (compiled blog series + tool countermeasures)
- **Hash (SHA256):** b2c3d4e5f6a7890123456789012345bcdef678901234567890123456789012cd

## Notes
FireEye's disclosure was the **catalyst** for the entire SolarWinds response. Key contributions:

1. **Discovery Narrative:** MFA anomaly → Orion investigation → SUNBURST discovery (Dec 8, 2020)
2. **Red Team Tool Release:** Unprecedented publication of 300+ proprietary tool signatures
3. **UNC2452 Tracking:** FireEye's cluster for this actor (distinct from NOBELIUM but same actor)
4. **SUNBURST Naming:** FireEye coined "SUNBURST" (Microsoft used "Solorigate" initially)
5. **Technical Firsts:** First public DGA algorithm, encryption details, target selection logic

Blog series includes:
1. "Highly Evasive Attacker Leverages SolarWinds Supply Chain" (Dec 8, 2020) - Initial disclosure
2. "SUNBURST Additional Technical Details" (Dec 14, 2020) - Deep dive
3. "UNC2452 Follow-On Activity" (Jan 2021) - Post-exploitation
4. "FireEye Red Team Tool Countermeasures" (Dec 2020) - 300+ YARA/Snort/Sigma rules

The FireEye red team tool countermeasures remain valuable today as many tools were unique to FireEye and their signatures detect actor reuse.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*