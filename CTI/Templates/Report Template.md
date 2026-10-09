---
aliases: []
tags: [report, template]
type: report
classification: TLP:CLEAR
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - Intelligence Report

## Metadata
- **Report ID:** {{report-id}}
- **Title:** {{title}}
- **Type:** {{type}} (Threat Actor Profile/Campaign Analysis/Vulnerability Advisory/Threat Landscape/Strategic/Operational/Tactical)
- **Classification:** {{classification}} (TLP:CLEAR/TLP:GREEN/TLP:AMBER/TLP:AMBER+STRICT/TLP:RED)
- **Status:** {{status}} (Draft/Review/Final/Archived)
- **Author:** {{author}}
- **Reviewers:** {{reviewers}}
- **Date Created:** {{date-created}}
- **Date Published:** {{date-published}}
- **Version:** {{version}}
- **Confidence Level:** {{confidence}}

## Executive Summary
{{executive-summary}}

## Key Findings
1. {{finding-1}}
2. {{finding-2}}
3. {{finding-3}}

## Threat Actor(s)
| Actor | Confidence | Role | Link |
|-------|------------|------|------|
| [[CTI/Threat Actors/{{actor-1}}]] | {{conf-1}} | {{role-1}} | Profile |

## Campaign(s)
| Campaign | Period | Status | Link |
|----------|--------|--------|------|
| [[CTI/Campaigns/{{campaign-1}}]] | {{period-1}} | {{status-1}} | Profile |

## Malware/Tools
| Tool | Type | Capabilities | Link |
|------|------|--------------|------|
| [[CTI/Malware/{{malware-1}}]] | {{type-1}} | {{caps-1}} | Profile |

## Vulnerabilities Exploited
| CVE | CVSS | Exploitation Status | Link |
|-----|------|---------------------|------|
| {{cve-1}} | {{cvss-1}} | {{exploit-status-1}} | [[CTI/Vulnerabilities/{{cve-1}}]] |

## MITRE ATT&CK Techniques Observed
| Tactic | Technique ID | Technique Name | Observed |
|--------|--------------|----------------|----------|
| {{tactic-1}} | T{{id-1}} | {{name-1}} | Yes/No |

## Indicators of Compromise
> **Full IOC List:** [[CTI/IOCs/{{title}} IOCs]]

### Summary
| Type | Count | New |
|------|-------|-----|
| File Hashes | {{hash-count}} | {{new-hash}} |
| IP Addresses | {{ip-count}} | {{new-ip}} |
| Domains | {{domain-count}} | {{new-domain}} |
| URLs | {{url-count}} | {{new-url}} |
| Email Addresses | {{email-count}} | {{new-email}} |
| Registry Keys | {{reg-count}} | {{new-reg}} |
| Mutexes | {{mutex-count}} | {{new-mutex}} |

### High-Confidence IOCs
| Type | Value | Description | First Seen | Last Seen | Confidence |
|------|-------|-------------|------------|-----------|------------|
| {{type-1}} | {{value-1}} | {{desc-1}} | {{first-1}} | {{last-1}} | {{conf-1}} |

## Threat Landscape Context
### Geographic Targeting
{{geo-targeting}}

### Sector Targeting
{{sector-targeting}}

### Historical Activity
{{historical-activity}}

## Analysis
### Attribution Assessment
{{attribution-assessment}}

### Capability Assessment
{{capability-assessment}}

### Intent Assessment
{{intent-assessment}}

### Likelihood of Future Activity
{{likelihood}}

## Recommendations
### Immediate Actions (0-24 hours)
- {{immediate-1}}
- {{immediate-2}}

### Short-term Actions (1-7 days)
- {{short-1}}
- {{short-2}}

### Long-term Actions (30+ days)
- {{long-1}}
- {{long-2}}

### Detection Opportunities
| Detection Logic | Data Source | MITRE Technique |
|-----------------|-------------|-----------------|
| {{detection-1}} | {{source-1}} | T{{id-1}} |

### Mitigation Strategies
| Strategy | Priority | Effort | MITRE Mitigation |
|----------|----------|--------|------------------|
| {{strategy-1}} | {{priority-1}} | {{effort-1}} | M{{id-1}} |

## Intelligence Gaps
- {{gap-1}}
- {{gap-2}}

## Sources & References
| Source | Type | Date | Reliability | Relevance | Link |
|--------|------|------|-------------|-----------|------|
| {{source-1}} | {{type-1}} | {{date-1}} | {{rel-1}} | {{relv-1}} | {{link-1}} |

## Appendix
### Appendix A: Full IOC Table
> See: [[CTI/IOCs/{{title}} IOCs]]

### Appendix B: MITRE ATT&CK Navigator Layer
```json
{{navigator-layer}}
```

### Appendix C: Timeline
| Date | Event | Description |
|------|-------|-------------|
| {{date-1}} | {{event-1}} | {{desc-1}} |

## Distribution
| Recipient | Organization | Classification | Date Sent |
|-----------|--------------|----------------|-----------|
| {{recipient-1}} | {{org-1}} | {{class-1}} | {{date-1}} |

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*