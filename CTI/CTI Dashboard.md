# CTI Dashboard - Cyber Threat Intelligence Platform

> **Centralized CTI Knowledge Base** | Built with Obsidian + Dataview + Excalidraw + MarkMind
> *Based on TΞLΞMΞTRY's Obsidian CTI Methodology*

---

## 🎯 Quick Navigation

| Category | Count | Link |
|----------|-------|------|
| **Threat Actors** | `=this.threat_actor_count` | [[CTI/Threat Actors/]] |
| **Malware Families** | `=this.malware_count` | [[CTI/Malware/]] |
| **Campaigns** | `=this.campaign_count` | [[CTI/Campaigns/]] |
| **Vulnerabilities** | `=this.vuln_count` | [[CTI/Vulnerabilities/]] |
| **Incidents** | `=this.incident_count` | [[CTI/Incidents/]] |
| **Reports** | `=this.report_count` | [[CTI/Reports/]] |
| **IOC Collections** | `=this.ioc_count` | [[CTI/IOCs/]] |
| **TTPs** | `=this.ttp_count` | [[CTI/TTPs/]] |
| **Tools** | `=this.tool_count` | [[CTI/Tools/]] |
| **References** | `=this.ref_count` | [[CTI/References/]] |

---

## 📊 Live Statistics (Dataview)

### Threat Actor Activity by Type
```dataview
TABLE WITHOUT ID
  actor_type as "Type",
  length(rows) as "Count"
FROM "CTI/Threat Actors"
WHERE actor_type
GROUP BY actor_type
SORT length(rows) DESC
```

### Top 10 Most Active Threat Actors (by Campaigns)
```dataview
TABLE WITHOUT ID
  file.link as "Threat Actor",
  length(campaigns) as "Campaigns",
  length(malware) as "Malware Families",
  length(tools) as "Tools"
FROM "CTI/Threat Actors"
WHERE campaigns
SORT length(campaigns) DESC
LIMIT 10
```

### Malware by Type
```dataview
TABLE WITHOUT ID
  malware_type as "Malware Type",
  length(rows) as "Count"
FROM "CTI/Malware"
WHERE malware_type
GROUP BY malware_type
SORT length(rows) DESC
```

### Campaign Timeline (Last 20)
```dataview
TABLE WITHOUT ID
  file.link as "Campaign",
  threat_actors as "Threat Actors",
  start_date as "Start",
  end_date as "End",
  status as "Status"
FROM "CTI/Campaigns"
SORT start_date DESC
LIMIT 20
```

### Critical Vulnerabilities (CVSS ≥ 9.0)
```dataview
TABLE WITHOUT ID
  file.link as "CVE",
  cvss_score as "CVSS",
  severity as "Severity",
  exploited as "Exploited in Wild",
  patch_available as "Patched"
FROM "CTI/Vulnerabilities"
WHERE cvss_score >= 9.0
SORT cvss_score DESC
```

### Incident Status Overview
```dataview
TABLE WITHOUT ID
  status as "Status",
  length(rows) as "Count"
FROM "CTI/Incidents"
WHERE status
GROUP BY status
SORT length(rows) DESC
```

### IOC Collection Summary
```dataview
TABLE WITHOUT ID
  file.link as "IOC Collection",
  entity as "Entity",
  entity_type as "Type",
  status as "Status"
FROM "CTI/IOCs"
SORT file.mtime DESC
LIMIT 15
```

### TTP Coverage (Top MITRE Tactics)
```dataview
TABLE WITHOUT ID
  tactic as "Tactic",
  length(rows) as "Techniques Documented"
FROM "CTI/TTPs"
WHERE tactic
GROUP BY tactic
SORT length(rows) DESC
```

---

## 🔍 Quick Queries

### Recently Updated Notes (Last 7 Days)
```dataview
TABLE WITHOUT ID
  file.link as "Note",
  file.folder as "Folder",
  file.mtime as "Modified"
FROM "CTI"
WHERE file.mtime >= date(today) - dur(7 days)
SORT file.mtime DESC
LIMIT 20
```

### Threat Actors Targeting Specific Sector
```dataview
TABLE WITHOUT ID
  file.link as "Threat Actor",
  sectors as "Sectors"
FROM "CTI/Threat Actors"
WHERE contains(lower(sectors), "healthcare")
SORT file.name ASC
```

### Malware Used by Specific Threat Actor
```dataview
TABLE WITHOUT ID
  file.link as "Malware",
  malware_type as "Type",
  platform as "Platform"
FROM "CTI/Malware"
WHERE contains(threat_actors, "[[CTI/Threat Actors/APT1]]")
```

### Campaigns Using Specific Malware
```dataview
TABLE WITHOUT ID
  file.link as "Campaign",
  threat_actors as "Threat Actors",
  start_date as "Start"
FROM "CTI/Campaigns"
WHERE contains(malware, "[[CTI/Malware/Cobalt Strike]]")
SORT start_date DESC
```

---

## 🗺️ Visualizations

### Threat Landscape Graph
> Open the **Graph View** (Ctrl+G) and apply these filters:
> - **Tags:** `#threat-actor` `#malware` `#campaign`
> - **Groups:** Color by folder (Threat Actors=Red, Malware=Green, Campaigns=Blue)
> - **Filters:** Remove orphans, show only linked notes

### Campaign Attack Chain Canvas
> See: [[CTI/Canvas/SolarWinds Attack Chain.canvas]]
> See: [[CTI/Canvas/APT28 Election Interference.canvas]]

### Threat Actor Relationship Mind Map
> See: [[CTI/Excalidraw/Chinese APT Ecosystem.excalidraw]]
> See: [[CTI/Excalidraw/Russian APT Relationships.excalidraw]]

---

## 📋 Active Investigations

```dataview
TASK
FROM "CTI"
WHERE !completed AND (contains(text, "INVESTIGATE") OR contains(text, "TODO") OR contains(text, "ANALYZE"))
GROUP BY file.folder
```

---

## 📅 Recent Intelligence Reports

```dataview
TABLE WITHOUT ID
  file.link as "Report",
  type as "Type",
  classification as "TLP",
  date_published as "Published",
  author as "Author"
FROM "CTI/Reports"
WHERE date_published
SORT date_published DESC
LIMIT 10
```

---

## 🛠️ Tools by Category
```dataview
TABLE WITHOUT ID
  tool_type as "Category",
  length(rows) as "Count"
FROM "CTI/Tools"
WHERE tool_type
GROUP BY tool_type
SORT length(rows) DESC
```

## 📚 References by Type
```dataview
TABLE WITHOUT ID
  ref_type as "Type",
  length(rows) as "Count"
FROM "CTI/References"
WHERE ref_type
GROUP BY ref_type
SORT length(rows) DESC
```

---

## ⚙️ Plugin Configuration Status

| Plugin | Status | Purpose |
|--------|--------|---------|
| **Dataview** | ✅ Required | Live queries, statistics, tables |
| **Excalidraw** | ✅ Recommended | Attack chain diagrams, infrastructure maps |
| **Iconize** | ✅ Recommended | Custom folder/file icons |
| **MarkMind** | ✅ Recommended | Mind maps for campaign analysis |
| **Paste Image Rename** | ✅ Recommended | Auto-organize screenshots |
| **Persistent Graph** | ✅ Recommended | Maintain graph layout |

---

## 🔧 Maintenance

### Template Files
- [[CTI/Templates/Threat Actor Template.md]]
- [[CTI/Templates/Malware Template.md]]
- [[CTI/Templates/Campaign Template.md]]
- [[CTI/Templates/Vulnerability Template.md]]
- [[CTI/Templates/Incident Template.md]]
- [[CTI/Templates/Report Template.md]]
- [[CTI/Templates/IOC Template.md]]
- [[CTI/Templates/TTP Template.md]]
- [[CTI/Templates/Tool Template.md]]
- [[CTI/Templates/Reference Template.md]]

### Configuration Notes
- **Templates Folder:** `CTI/Templates/` (set in Settings → Templates)
- **Attachments Folder:** `CTI/Attachments/` (set in Settings → Files & Links)
- **New File Location:** Folder of current file (recommended)

### Dataview Index
Run `Dataview: Rebuild Index` command if queries show stale data.

---

## 📚 Methodology References

- **Primary:** [TΞLΞMΞTRY - Mastering CTI with Obsidian](https://github.com/t3l3m3try/Obsidian_Templates)
- **MITRE ATT&CK:** https://attack.mitre.org/
- **STIX/TAXII:** https://oasis-open.github.io/cti-documentation/
- **MISP:** https://www.misp-project.org/

---

*Last updated: `=dateformat(date(now), "YYYY-MM-DD")`*
*Vault: `=this.app.vault.getName()`*