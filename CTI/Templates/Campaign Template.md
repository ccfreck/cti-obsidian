---
aliases: []
tags: [campaign, template]
type: campaign
status: active
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - Campaign Profile

## Overview
- **Name:** {{title}}
- **Aliases:** {{aliases}}
- **Threat Actor(s):** [[CTI/Threat Actors/{{actor-1}}]], [[CTI/Threat Actors/{{actor-2}}]]
- **Start Date:** {{start-date}}
- **End Date:** {{end-date}} (or "Ongoing")
- **Status:** {{status}} (active/dormant/completed)
- **Confidence Level:** {{confidence}}

## Description
{{description}}

## Objectives
- **Primary Objective:** {{primary-objective}}
- **Secondary Objectives:** {{secondary-objectives}}

## Targeting
### Victims
| Victim | Sector | Country | Compromise Date | Impact |
|--------|--------|---------|-----------------|--------|
| {{victim-1}} | {{sector}} | {{country}} | {{date}} | {{impact}} |

### Geographic Scope
{{geographic-scope}}

### Sector Focus
{{sector-focus}}

## Attack Chain (MITRE ATT&CK)
| Phase | Technique ID | Technique Name | Description | Tools/Malware |
|-------|--------------|----------------|-------------|---------------|
| Initial Access | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Execution | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Persistence | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Privilege Escalation | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Defense Evasion | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Credential Access | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Discovery | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Lateral Movement | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Collection | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Exfiltration | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |
| Command & Control | T{{id}} | {{name}} | {{desc}} | [[CTI/Malware/{{tool}}]] |

## Infrastructure
### Command & Control
- **Domains:** {{c2-domains}}
- **IPs:** {{c2-ips}}
- **Protocols:** {{c2-protocols}}

### Delivery Infrastructure
- **Phishing Domains:** {{phishing-domains}}
- **Exploit Servers:** {{exploit-servers}}
- **File Hosting:** {{file-hosting}}

### Operational Infrastructure
- **VPN/Proxy:** {{vpn-proxy}}
- **Staging Servers:** {{staging}}
- **Data Exfiltration:** {{exfil}}

## Malware & Tools Used
| Tool/Malware | Type | Role in Campaign | Link |
|--------------|------|------------------|------|
| {{tool-1}} | {{type}} | {{role}} | [[CTI/Malware/{{tool-1}}]] |
| {{tool-2}} | {{type}} | {{role}} | [[CTI/Tools/{{tool-2}}]] |

## IOCs Summary
> **Full IOC List:** [[CTI/IOCs/{{title}} IOCs]]

| Type | Count | Examples |
|------|-------|----------|
| File Hashes | {{hash-count}} | {{hash-examples}} |
| IP Addresses | {{ip-count}} | {{ip-examples}} |
| Domains | {{domain-count}} | {{domain-examples}} |
| URLs | {{url-count}} | {{url-examples}} |
| Email Addresses | {{email-count}} | {{email-examples}} |

## Timeline
| Date | Event | Description | Source |
|------|-------|-------------|--------|
| {{date-1}} | {{event-1}} | {{desc-1}} | {{source-1}} |
| {{date-2}} | {{event-2}} | {{desc-2}} | {{source-2}} |

## Attribution Analysis
- **Attribution Confidence:** {{attribution-confidence}}
- **Key Evidence:** {{evidence}}
- **Alternative Hypotheses:** {{alternatives}}

## Impact Assessment
- **Organizations Compromised:** {{org-count}}
- **Data Stolen:** {{data-stolen}}
- **Financial Impact:** {{financial-impact}}
- **Operational Impact:** {{operational-impact}}

## Intelligence Sources
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| {{source-name}} | {{source-type}} | {{source-date}} | {{reliability}} | {{source-link}} |

## Related Campaigns
- [[CTI/Campaigns/{{related-1}}]]
- [[CTI/Campaigns/{{related-2}}]]

## Notes & Analysis
{{notes}}

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*