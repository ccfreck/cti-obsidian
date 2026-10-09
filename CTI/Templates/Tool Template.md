---
aliases: []
tags: [tool, template]
type: tool
status: active
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - Tool Profile

## Overview
- **Name:** {{title}}
- **Aliases:** {{aliases}}
- **Type:** {{type}} (C2 Framework, Post-Exploitation, Recon, Credential Access, Lateral Movement, Exfiltration, Utility, etc.)
- **Category:** {{category}} (Offensive, Defensive, Dual-Use)
- **Language:** {{language}} (C, C++, C#, Go, Rust, Python, PowerShell, Bash, etc.)
- **Platform:** {{platform}} (Windows, Linux, macOS, Cross-platform)
- **License:** {{license}} (Open Source/Commercial/Closed Source/Leaked)
- **Developer:** {{developer}}
- **First Released:** {{first-released}}
- **Latest Version:** {{latest-version}}
- **Status:** {{status}} (Active/Maintained/Deprecated/Archived)
- **Confidence Level:** {{confidence}}

## Description
{{description}}

## Capabilities
| Capability | Description | MITRE ATT&CK |
|------------|-------------|--------------|
| {{cap-1}} | {{cap-desc-1}} | T{{tech-id-1}} |
| {{cap-2}} | {{cap-desc-2}} | T{{tech-id-2}} |

## Technical Details
### Architecture
- **Architecture:** {{architecture}}
- **Dependencies:** {{dependencies}}
- **Installation:** {{installation}}
- **Configuration:** {{configuration}}

### Command & Control (if applicable)
- **C2 Protocol:** {{c2-protocol}}
- **Encryption:** {{encryption}}
- **Proxy Support:** {{proxy-support}}
- **Domain Fronting:** {{domain-fronting}}

### Modules/Plugins
| Module | Description | Capabilities |
|--------|-------------|--------------|
| {{module-1}} | {{mod-desc-1}} | {{mod-caps-1}} |

## Usage
### Basic Usage
```bash
{{basic-usage}}
```

### Common Commands
| Command | Description | Example |
|---------|-------------|---------|
| {{cmd-1}} | {{cmd-desc-1}} | {{cmd-ex-1}} |

### Configuration Examples
```json
{{config-example}}
```

## Detection
### File Indicators
| Hash Type | Value | Context |
|-----------|-------|---------|
| MD5 | {{md5}} | {{md5-ctx}} |
| SHA256 | {{sha256}} | {{sha256-ctx}} |

### Network Indicators
- **Default Ports:** {{ports}}
- **Protocol Patterns:** {{proto-patterns}}
- **Certificate Details:** {{cert-details}}

### Behavioral Indicators
- {{behavior-1}}
- {{behavior-2}}

### YARA Rules
```yara
{{yara-rule}}
```

### Sigma Rules
```yaml
{{sigma-rule}}
```

## Threat Intelligence
### Threat Actors Using This Tool
| Actor | Confidence | Campaigns | Version Used |
|-------|------------|-----------|--------------|
| [[CTI/Threat Actors/{{actor-1}}]] | {{conf-1}} | [[CTI/Campaigns/{{campaign-1}}]] | {{version-1}} |

### Malware Families Using/Dropping This
| Malware | Relationship | Details |
|---------|--------------|---------|
| [[CTI/Malware/{{malware-1}}]] | {{rel-1}} | {{details-1}} |

## Legitimate Use Cases
- {{legitimate-use-1}}
- {{legitimate-use-2}}

## Attribution Challenges
{{attribution-challenges}}

## Variants & Forks
| Variant | Developer | Description | Link |
|---------|-----------|-------------|------|
| {{variant-1}} | {{dev-1}} | {{desc-1}} | {{link-1}} |

## References
| Source | Type | Date | Link |
|--------|------|------|------|
| {{source-1}} | {{type-1}} | {{date-1}} | {{link-1}} |
| GitHub | Repository | {{date}} | {{github-link}} |

## Analysis Notes
{{notes}}

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*