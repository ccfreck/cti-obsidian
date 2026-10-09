---
aliases: []
tags: [ioc, template]
type: ioc-collection
status: active
confidence: high
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
---

# {{title}} - IOC Collection

## Metadata
- **Collection ID:** {{collection-id}}
- **Title:** {{title}}
- **Associated Entity:** {{entity}} (Threat Actor/Campaign/Malware/Incident)
- **Entity Link:** [[CTI/{{entity-type}}/{{entity}}]]
- **Classification:** {{classification}} (TLP:CLEAR/TLP:GREEN/TLP:AMBER/TLP:RED)
- **Status:** {{status}} (Active/Historical/Revoked)
- **Confidence Level:** {{confidence}}
- **Created:** {{date-created}}
- **Last Updated:** {{date-updated}}
- **Analyst:** {{analyst}}

## Source Information
| Source | Type | Date | Reliability | Link |
|--------|------|------|-------------|------|
| {{source-1}} | {{type-1}} | {{date-1}} | {{rel-1}} | {{link-1}} |

## File Indicators
### Hashes
| Hash Type | Value | Filename | Size | First Seen | Last Seen | Confidence | Context |
|-----------|-------|----------|------|------------|-----------|------------|---------|
| MD5 | {{md5-1}} | {{file-1}} | {{size-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} |
| SHA1 | {{sha1-1}} | {{file-1}} | {{size-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} |
| SHA256 | {{sha256-1}} | {{file-1}} | {{size-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} |
| IMPHASH | {{imphash-1}} | {{file-1}} | {{size-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} |

### File Metadata
| Filename | Description | Type | Compiler | Timestamp | Sections |
|----------|-------------|------|----------|-----------|----------|
| {{file-1}} | {{desc-1}} | {{type-1}} | {{compiler-1}} | {{ts-1}} | {{sections-1}} |

## Network Indicators
### IP Addresses
| IP Address | Port(s) | Protocol | Direction | First Seen | Last Seen | Confidence | Context | ASN | Geo |
|------------|---------|----------|-----------|------------|-----------|------------|---------|-----|-----|
| {{ip-1}} | {{port-1}} | {{proto-1}} | {{dir-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} | {{asn-1}} | {{geo-1}} |

### Domains
| Domain | Type | First Seen | Last Seen | Confidence | Context | Registrar | Creation Date | IP Resolution |
|--------|------|------------|-----------|------------|---------|-----------|---------------|---------------|
| {{domain-1}} | {{type-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} | {{registrar-1}} | {{created-1}} | {{ip-res-1}} |

### URLs
| URL | Domain | Path | First Seen | Last Seen | Confidence | Context | Content Type |
|-----|--------|------|------------|-----------|------------|---------|--------------|
| {{url-1}} | {{domain-1}} | {{path-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} | {{content-1}} |

### Email Indicators
| Email Address | Type | First Seen | Last Seen | Confidence | Context | Subject | Attachments |
|---------------|------|------------|-----------|------------|---------|---------|-------------|
| {{email-1}} | {{type-1}} | {{first-1}} | {{last-1}} | {{conf-1}} | {{ctx-1}} | {{subject-1}} | {{attach-1}} |

## Host Indicators
### Registry Keys
| Registry Path | Value Name | Value Data | Type | First Seen | Confidence | Context |
|---------------|------------|------------|------|------------|------------|---------|
| {{reg-path-1}} | {{val-name-1}} | {{val-data-1}} | {{type-1}} | {{first-1}} | {{conf-1}} | {{ctx-1}} |

### Mutexes
| Mutex Name | Description | First Seen | Confidence | Context |
|------------|-------------|------------|------------|---------|
| {{mutex-1}} | {{desc-1}} | {{first-1}} | {{conf-1}} | {{ctx-1}} |

### File Paths
| Path | Description | First Seen | Confidence | Context |
|------|-------------|------------|------------|---------|
| {{path-1}} | {{desc-1}} | {{first-1}} | {{conf-1}} | {{ctx-1}} |

### Scheduled Tasks
| Task Name | Description | Command | First Seen | Confidence | Context |
|-----------|-------------|---------|------------|------------|---------|
| {{task-1}} | {{desc-1}} | {{cmd-1}} | {{first-1}} | {{conf-1}} | {{ctx-1}} |

### Services
| Service Name | Display Name | Path | Description | First Seen | Confidence | Context |
|--------------|--------------|------|-------------|------------|------------|---------|
| {{svc-1}} | {{display-1}} | {{path-1}} | {{desc-1}} | {{first-1}} | {{conf-1}} | {{ctx-1}} |

### Certificates
| SHA1 | SHA256 | Subject | Issuer | Valid From | Valid To | First Seen | Context |
|------|--------|---------|--------|------------|----------|------------|---------|
| {{cert-sha1-1}} | {{cert-sha256-1}} | {{subject-1}} | {{issuer-1}} | {{from-1}} | {{to-1}} | {{first-1}} | {{ctx-1}} |

## Detection Rules
### YARA
```yara
{{yara-rule}}
```

### Sigma
```yaml
{{sigma-rule}}
```

### Snort/Suricata
```
{{ids-rule}}
```

### STIX/TAXII
```json
{{stix-bundle}}
```

## Enrichment
### VirusTotal
| Hash | Detections | Last Analysis | Link |
|------|------------|---------------|------|
| {{hash-1}} | {{detections-1}}/{{total-1}} | {{date-1}} | {{link-1}} |

### Passive DNS
| Domain | IP | First Seen | Last Seen | Source |
|--------|----|------------|-----------|--------|
| {{domain-1}} | {{ip-1}} | {{first-1}} | {{last-1}} | {{source-1}} |

### WHOIS
| Domain | Registrar | Creation | Expiration | Registrant | Nameservers |
|--------|-----------|----------|------------|------------|-------------|
| {{domain-1}} | {{registrar-1}} | {{created-1}} | {{expires-1}} | {{registrant-1}} | {{ns-1}} |

## Sharing & Distribution
| Format | Generated | Recipients | Classification |
|--------|-----------|------------|----------------|
| STIX 2.1 | {{date}} | {{recipients}} | {{classification}} |
| MISP | {{date}} | {{recipients}} | {{classification}} |
| CSV | {{date}} | {{recipients}} | {{classification}} |
| JSON | {{date}} | {{recipients}} | {{classification}} |

## Notes
{{notes}}

---
*Template based on TΞLΞMΞTRY's Obsidian CTI methodology*
*Last updated: {{date:YYYY-MM-DD}}*