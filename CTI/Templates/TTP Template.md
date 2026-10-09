---
aliases: []
tags: [ttp, template, mitre-attack]
type: ttp
status: active
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - TTP Profile

## Metadata
- **Technique ID:** T{{technique-id}} (e.g., T1059, T1059.001)
- **Name:** {{title}}
- **Tactic(s):** {{tactics}} (comma-separated: Initial Access, Execution, Persistence, etc.)
- **Platform(s):** {{platforms}} (Windows, Linux, macOS, Network, Cloud, Containers, etc.)
- **Permissions Required:** {{permissions}} (User, Administrator, SYSTEM, root, etc.)
- **Data Sources:** {{data-sources}} (Process monitoring, File monitoring, Network traffic, etc.)
- **Version:** {{version}}
- **Confidence Level:** {{confidence}}
- **Created:** {{date-created}}
- **Last Updated:** {{date-updated}}

## Description
{{description}}

## MITRE ATT&CK Reference
- **Official Page:** https://attack.mitre.org/techniques/T{{technique-id}}/
- **Parent Technique:** T{{parent-id}} (if sub-technique)
- **Sub-techniques:** T{{sub-id-1}}, T{{sub-id-2}}

## Procedure Examples
| Procedure | Description | Threat Actor | Malware/Tool | Reference |
|-----------|-------------|--------------|--------------|-----------|
| {{proc-1}} | {{proc-desc-1}} | [[CTI/Threat Actors/{{actor-1}}]] | [[CTI/Malware/{{malware-1}}]] | {{ref-1}} |
| {{proc-2}} | {{proc-desc-2}} | [[CTI/Threat Actors/{{actor-2}}]] | [[CTI/Tools/{{tool-1}}]] | {{ref-2}} |

## Detection
### Detection Logic
{{detection-logic}}

### Data Sources Required
| Data Source | Components | Coverage |
|-------------|------------|----------|
| {{source-1}} | {{components-1}} | {{coverage-1}} |

### Sigma Rules
```yaml
{{sigma-rule}}
```

### Splunk/Elastic/KQL Queries
```splunk
{{splunk-query}}
```

### Elastic/Opensearch
```json
{{elastic-query}}
```

### KQL (Sentinel/Defender)
```kql
{{kql-query}}
```

### False Positives
- {{fp-1}}
- {{fp-2}}

### False Negatives
- {{fn-1}}
- {{fn-2}}

## Mitigation
| Mitigation ID | Mitigation Name | Description | Effectiveness |
|---------------|-----------------|-------------|---------------|
| M{{mit-id-1}} | {{mit-name-1}} | {{mit-desc-1}} | {{eff-1}} |
| M{{mit-id-2}} | {{mit-name-2}} | {{mit-desc-2}} | {{eff-2}} |

### Specific Mitigations for This Technique
{{specific-mitigations}}

## Threat Intelligence
### Threat Actors Using This Technique
| Actor | Confidence | Campaigns | First Observed | Last Observed |
|-------|------------|-----------|----------------|---------------|
| [[CTI/Threat Actors/{{actor-1}}]] | {{conf-1}} | [[CTI/Campaigns/{{campaign-1}}]] | {{first-1}} | {{last-1}} |

### Malware/Tools Implementing This
| Tool/Malware | Type | Version | Implementation Details |
|--------------|------|---------|------------------------|
| [[CTI/Malware/{{malware-1}}]] | {{type-1}} | {{version-1}} | {{details-1}} |

### Campaigns Leveraging This
| Campaign | Date | Details |
|----------|------|---------|
| [[CTI/Campaigns/{{campaign-1}}]] | {{date-1}} | {{details-1}} |

## Red Team / Adversary Emulation
### Atomic Test
```yaml
{{atomic-test}}
```

### Execution Command Examples
```bash
{{cmd-example-1}}
```
```powershell
{{ps-example-1}}
```

### Prerequisites
- {{prereq-1}}
- {{prereq-2}}

### Cleanup
{{cleanup}}

## Related Techniques
| Technique ID | Name | Relationship |
|--------------|------|--------------|
| T{{related-1}} | {{related-name-1}} | {{relationship-1}} |

## ATT&CK Navigator Layer
```json
{
  "version": "4.5",
  "name": "{{title}}",
  "description": "Techniques related to {{title}}",
  "domain": "enterprise-attack",
  "techniques": [
    {
      "techniqueID": "T{{technique-id}}",
      "color": "#ff6600",
      "comment": "{{title}}"
    }
  ],
  "gradient": {
    "colors": ["#ffffff", "#ff6600"],
    "minValue": 0,
    "maxValue": 100
  }
}
```

## References
| Source | Type | Date | Link |
|--------|------|------|------|
| MITRE ATT&CK | Official | {{date}} | https://attack.mitre.org/techniques/T{{technique-id}}/ |
| {{source-1}} | {{type-1}} | {{date-1}} | {{link-1}} |

## Notes & Analysis
{{notes}}

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*