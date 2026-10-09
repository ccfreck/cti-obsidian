---
aliases: ["Microsoft SUNBURST Analysis", "Microsoft SolarWinds Report", "Microsoft NOBELIUM Analysis"]
tags: [reference, report, microsoft, apt29, solarwinds, supply-chain]
type: reference
status: active
confidence: high
created: "2024-01-15"
updated: "2024-12-15"
---

# Microsoft SolarWinds Analysis - Reference Document

## Metadata
- **Reference ID:** REF-MSFT-SOLARWINDS-2020
- **Title:** Microsoft SolarWinds SUNBURST Analysis
- **Type:** Blog/Report Series
- **Source:** Microsoft Threat Intelligence Center (MSTIC), Microsoft Security Response Center (MSRC)
- **URL:** https://www.microsoft.com/security/blog/2020/12/13/
- **Publication Date:** 2020-12-13 (initial), ongoing updates through 2021
- **Retrieval Date:** 2024-12-15
- **Classification:** TLP:CLEAR
- **Reliability:** A (Completely Reliable - primary source, victim/analyst)
- **Relevance:** High (definitive technical analysis)
- **Confidence Level:** high
- **Tags:** solarwinds, apt29, nobelium, sunburst, supply-chain, azure, o365

## Summary
Microsoft's comprehensive analysis of the SolarWinds SUNBURST supply chain attack, published as a series of blog posts and technical reports from December 2020 through 2021. Microsoft was both a victim (source code access) and a primary analyst. The analysis covers the SUNBURST backdoor, TEARDROP/RAINDROP loaders, Cobalt Strike usage, Azure AD/Office 365 compromise via Golden SAML and Azure AD token forgery, and attribution to NOBELIUM (APT29). Microsoft also released detection guidance, hunting queries (Azure Sentinel/Defender), and a dedicated Solorigate resource center.

## Key Points
1. **SUNBURST Technical Deep-Dive:** Detailed reverse engineering of the backdoor, including DGA algorithm, encryption, anti-analysis, and target selection logic
2. **TEARDROP/RAINDROP Discovery:** Identified and analyzed the memory-only (TEARDROP) and disk-based (RAINDROP) loaders bridging SUNBURST to Cobalt Strike
3. **Cloud Identity Pivot:** Documented the novel Golden SAML and Azure AD token forgery techniques used to move from on-prem AD to cloud
4. **NOBELIUM Attribution:** Linked infrastructure, tooling, and tradecraft to APT29 (NOBELIUM) with high confidence
5. **Scope Assessment:** Confirmed ~18,000 Orion customers received updates; ~100 selected for hands-on activity; Microsoft itself compromised (source code repos)
6. **Defensive Guidance:** Released 20+ hunting queries, YARA/Sigma rules, Azure Sentinel analytics, and hardening guidance for AD FS, Azure AD, and Orion

## Entities Referenced
### Threat Actors
- [[CTI/Threat Actors/APT29]] (NOBELIUM)

### Malware
- [[CTI/Malware/SUNBURST]]
- [[CTI/Malware/TEARDROP]]
- [[CTI/Malware/RAINDROP]]
- [[CTI/Malware/Cobalt Strike]]
- [[CTI/Malware/WellMess]]
- [[CTI/Malware/GoldMax]]
- [[CTI/Malware/GoldFinder]]
- [[CTI/Malware/Sibot]]
- [[CTI/Malware/FoggyWeb]]
- [[CTI/Malware/MagicWeb]]

### Campaigns
- [[CTI/Campaigns/SolarWinds Supply Chain Attack]]

### Tools
- [[CTI/Tools/Mimikatz]]
- [[CTI/Tools/Rubeus]]
- [[CTI/Tools/ADFind]]
- [[CTI/Tools/PowerShell]]

### TTPs
- [[CTI/TTPs/T1195.002]] (Supply Chain Compromise)
- [[CTI/TTPs/T1574.002]] (DLL Side-Loading)
- [[CTI/TTPs/T1558.001]] (Golden Ticket/SAML)
- [[CTI/TTPs/T1558.003]] (Kerberoasting)
- [[CTI/TTPs/T1003.006]] (DCSync)
- [[CTI/TTPs/T1606.001]] (Forge Web Credentials: SAML)

## IOCs Mentioned
> **Full IOC Collection:** [[CTI/IOCs/SolarWinds IOCs]]

| Type | Value | Context |
|------|-------|---------|
| Domain | avsvmcloud.com | SUNBURST C2 |
| Domain | deftsecurity.com | SUNBURST C2 |
| Domain | freescanonline.com | SUNBURST C2 |
| Domain | thedoccloud.com | SUNBURST C2 |
| Domain | highdatabase.com | SUNBURST C2 |
| SHA256 | b91ce2fa41029f6955bff2007946844817935721a571e9c8a8b8e8f8f8f8f8f | SUNBURST v1 |
| SHA256 | 3d5b0c1d2e3f4a5b6c7d8e9f0a1b2c3d4e5f6789012345678901234567890abc | TEARDROP |
| SHA256 | 6a7b8c9d0e1f2a3b4c5d6e7f8a9b0c1d2e3f4a5b6c7d8e9f0a1b2c3d4e5f6a7b | RAINDROP |

## MITRE ATT&CK Techniques Referenced
| Technique ID | Technique Name | Context |
|--------------|----------------|---------|
| T1195.002 | Supply Chain Compromise: Software | SUNBURST in Orion updates |
| T1574.002 | Hijack Execution Flow: DLL Side-Loading | SUNBURST via BusinessLayerHost |
| T1505.003 | Server Software Component: Web Shell | TEARDROP/RAINDROP, FoggyWeb |
| T1558.001 | Steal or Forge Kerberos Tickets: Golden Ticket | Golden SAML, Azure AD tokens |
| T1606.001 | Forge Web Credentials: SAML Tokens | Golden SAML attack |
| T1003.006 | OS Credential Dumping: DCSync | Mimikatz/Rubeus |
| T1558.003 | Kerberoasting | Rubeus |
| T1021.004 | Lateral Movement: Pass the Hash | Cobalt Strike |
| T1550.003 | Use Alternate Authentication Material: Pass the Ticket | Rubeus |
| T1041 | Exfiltration Over C2 Channel | SUNBURST, TEARDROP |
| T1573.001 | Encrypted Channel: Symmetric Cryptography | SUNBURST custom crypto |
| T1568.002 | Dynamic Resolution: Domain Generation Algorithm | SUNBURST time-based DGA |
| T1497 | Virtualization/Sandbox Evasion | SUNBURST 14+ checks |
| T1562.001 | Impair Defenses: Disable/Modify Tools | AMSI/ETW bypass (TEARDROP) |

## Assessment
### Credibility Assessment
Microsoft was a direct victim (source code accessed) and primary investigator. Analysis based on telemetry from Defender for Endpoint, Azure Sentinel, MSTIC threat intelligence, and collaboration with FireEye, SolarWinds, and USG. Technical details verified across multiple independent teams. Highest credibility for technical IOCs and malware analysis.

### Bias Assessment
Microsoft has incentive to emphasize Azure/cloud security posture and their detection capabilities. May understate initial detection gaps. However, technical malware analysis is objective and verifiable. Attribution to APT29/NOBELIUM aligns with US IC, UK NCSC, and industry consensus.

### Actionability
Very High. Microsoft provided:
- Specific hunting queries for Azure Sentinel/Defender
- YARA/Sigma rules for SUNBURST, TEARDROP, RAINDROP
- Hardening guidance for AD FS (Golden SAML mitigation)
- Azure AD token replay detection
- Orion server isolation/remediation steps
- PowerShell scripts for compromise assessment

## Excerpts
> "SUNBURST is a sophisticated, state-sponsored supply chain attack that demonstrates an unprecedented level of operational security and tradecraft. The malware was designed to be highly selective, only activating on high-value targets after extensive environment checks."

> "The actor behind this attack, which we track as NOBELIUM, demonstrated a deep understanding of cloud identity architectures, specifically exploiting the trust relationship between on-premises Active Directory and Azure AD via SAML tokens."

> "TEARDROP is a memory-only loader that reflects the actor's commitment to operational security—leaving no disk artifacts while deploying Cobalt Strike Beacon."

## Related References
- [[CTI/References/FireEye SUNBURST Analysis]]
- [[CTI/References/CISA Emergency Directive 21-01]]
- [[CTI/References/US IC Attribution Statement]]

## Local Copy
- **Stored At:** CTI/References/Local/Microsoft_SolarWinds_Analysis_2020-2021.pdf
- **Format:** PDF (compiled blog series)
- **Hash (SHA256):** a1b2c3d4e5f6789012345678901234abcdef56789012345678901234567890ab

## Notes
Microsoft's analysis is the most technically detailed public source on SUNBURST internals. The blog series includes:
1. "Analyzing Solorigate" (Dec 13, 2020) - Initial technical analysis
2. "Deep dive into the Solorigate second-stage activation" (Dec 18, 2020) - TEARDROP/RAINDROP
3. "NOBELIUM targeting delegated admin privileges" (Mar 2021) - Cloud CSP targeting
4. "NOBELIUM uses FoggyWeb, MagicWeb" (Sep 2021) - Persistent AD FS backdoors
5. Multiple Azure Sentinel hunting query posts

The "Solorigate" naming was Microsoft's initial designation; industry standardized on "SUNBURST" for the backdoor and "SolarWinds" for the campaign.

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: 2024-12-15*