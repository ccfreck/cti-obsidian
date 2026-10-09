---
aliases: []
tags: [threat-actor, template]
type: threat-actor
status: active
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - Threat Actor Profile

## Overview
- **Name:** {{title}}
- **Aliases:** {{aliases}}
- **Type:** {{type}} (e.g., APT, Cybercrime, Hacktivist, Nation-State)
- **Origin/Country:** {{origin}}
- **First Observed:** {{first-observed}}
- **Last Activity:** {{last-activity}}
- **Status:** {{status}} (active/dormant/disbanded)
- **Confidence Level:** {{confidence}}

## Description
{{description}}

## Goals & Motivation
- **Primary Goal:** {{primary-goal}} (espionage, financial gain, disruption, etc.)
- **Secondary Goals:** {{secondary-goals}}
- **Motivation:** {{motivation}}

## Targeting
### Sectors Targeted
- {{sectors}}

### Geographic Targeting
- {{geographic-targeting}}

### Notable Victims
- {{victims}}

## Capabilities & Resources
- **Sophistication Level:** {{sophistication}} (low/medium/high/advanced)
- **Funding Source:** {{funding}}
- **Team Size:** {{team-size}}
- **Infrastructure:** {{infrastructure}}

## TTPs (MITRE ATT&CK Mapping)
| Technique ID | Technique Name | Description | Sub-techniques |
|--------------|----------------|-------------|----------------|
| T{{technique-id}} | {{technique-name}} | {{technique-desc}} | {{sub-techniques}} |

> **Related TTPs:** [[CTI/TTPs/]] 

## Malware & Tools Used
| Malware/Tool | Type | Description | Links |
|--------------|------|-------------|-------|
| {{malware-name}} | {{malware-type}} | {{malware-desc}} | [[CTI/Malware/{{malware-name}}]] |

> **See also:** [[CTI/Malware/]], [[CTI/Tools/]]

## Infrastructure & IOCs
### Command & Control
- **C2 Domains:** {{c2-domains}}
- **C2 IPs:** {{c2-ips}}
- **Protocols:** {{c2-protocols}}

### Host-Based IOCs
- **File Hashes:** {{file-hashes}}
- **Registry Keys:** {{registry-keys}}
- **Mutexes:** {{mutexes}}
- **File Paths:** {{file-paths}}

### Network IOCs
- **IP Addresses:** {{network-ips}}
- **Domains:** {{network-domains}}
- **URLs:** {{network-urls}}

> **Full IOC List:** [[CTI/IOCs/{{title}} IOCs]]

## Associated Campaigns
- [[CTI/Campaigns/{{campaign-1}}]]
- [[CTI/Campaigns/{{campaign-2}}]]

## Attribution & Relationships
- **Attributed To:** {{attribution}}
- **Related Actors:** {{related-actors}}
- **Collaborations:** {{collaborations}}

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| {{source-name}} | {{source-type}} | {{source-date}} | {{reliability}} | {{source-link}} |

## Notes & Analysis
{{notes}}

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*