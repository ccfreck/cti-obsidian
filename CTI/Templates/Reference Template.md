---
aliases: []
tags: [reference, template]
type: reference
status: active
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - Reference Document

## Metadata
- **Reference ID:** {{ref-id}}
- **Title:** {{title}}
- **Type:** {{type}} (Report/Whitepaper/Blog/Advisory/Research/News/Standard/Framework)
- **Source:** {{source}} (Organization/Author)
- **URL:** {{url}}
- **Publication Date:** {{pub-date}}
- **Retrieval Date:** {{retrieval-date}}
- **Classification:** {{classification}} (TLP:CLEAR/TLP:GREEN/TLP:AMBER/TLP:RED)
- **Reliability:** {{reliability}} (A-F scale: A=Completely Reliable, F=Cannot Be Judged)
- **Relevance:** {{relevance}} (High/Medium/Low)
- **Confidence Level:** {{confidence}}
- **Tags:** {{tags}}

## Summary
{{summary}}

## Key Points
1. {{point-1}}
2. {{point-2}}
3. {{point-3}}

## Entities Referenced
### Threat Actors
- [[CTI/Threat Actors/{{actor-1}}]]
- [[CTI/Threat Actors/{{actor-2}}]]

### Malware
- [[CTI/Malware/{{malware-1}}]]
- [[CTI/Malware/{{malware-2}}]]

### Campaigns
- [[CTI/Campaigns/{{campaign-1}}]]

### Vulnerabilities
- [[CTI/Vulnerabilities/{{cve-1}}]]

### Tools
- [[CTI/Tools/{{tool-1}}]]

### TTPs
- [[CTI/TTPs/T{{technique-id}}]]

## IOCs Mentioned
> **Full IOC Collection:** [[CTI/IOCs/{{title}} IOCs]]

| Type | Value | Context |
|------|-------|---------|
| {{type-1}} | {{value-1}} | {{ctx-1}} |

## MITRE ATT&CK Techniques Referenced
| Technique ID | Technique Name | Context |
|--------------|----------------|---------|
| T{{tech-id-1}} | {{tech-name-1}} | {{tech-ctx-1}} |

## Assessment
### Credibility Assessment
{{credibility-assessment}}

### Bias Assessment
{{bias-assessment}}

### Actionability
{{actionability}}

## Excerpts
> {{excerpt-1}}

> {{excerpt-2}}

## Related References
- [[CTI/References/{{related-1}}]]
- [[CTI/References/{{related-2}}]]

## Local Copy
- **Stored At:** {{local-path}}
- **Format:** {{format}} (PDF/HTML/Markdown/Text)
- **Hash (SHA256):** {{sha256}}

## Notes
{{notes}}

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*