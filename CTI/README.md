# CTI Feed - Cyber Threat Intelligence Platform

> **A comprehensive CTI knowledge base built in Obsidian**
> *Based on [TΞLΞMΞTRY's methodology](https://github.com/t3l3m3try/Obsidian_Templates)*

---

## 🎯 Overview

This vault transforms Obsidian into a **local-first, free, and powerful CTI platform** for:
- Threat actor profiling and tracking
- Malware analysis and cataloging
- Campaign mapping and timeline analysis
- Vulnerability management
- Incident response documentation
- Intelligence report generation
- IOC collection and sharing
- TTP documentation (MITRE ATT&CK aligned)
- Tool cataloging
- Reference library

---

## 🚀 Quick Start

### 1. Open the Vault
```bash
# In Obsidian: File → Open Vault → Select this folder
```

### 2. Install Required Plugins
See [Plugin Configuration Guide](CTI/Plugin%20Configuration%20Guide.md) for detailed setup.

**Essential Plugins:**
| Plugin | Purpose | Required |
|--------|---------|----------|
| **Dataview** | Live queries, dashboards, statistics | ✅ Yes |
| **Excalidraw** | Attack chains, infrastructure maps | ✅ Yes |
| **Iconize** | Visual folder/file organization | ✅ Recommended |
| **MarkMind** | Mind maps for campaign analysis | ✅ Recommended |
| **Paste Image Rename** | Auto-organize screenshots | ✅ Recommended |
| **Persistent Graph** | Maintain graph layout | ✅ Recommended |

### 3. Configure Settings
1. **Templates Folder:** `CTI/Templates/` (Settings → Templates)
2. **Attachments Folder:** `CTI/Attachments/` (Settings → Files & Links)
3. **New File Location:** "Folder of current file"

### 4. Start with the Dashboard
Open [[CTI/CTI Dashboard.md]] - your main entry point with live statistics.

---

## 📁 Vault Structure

```
CTI/
├── CTI Dashboard.md              # 🏠 Main entry point with Dataview queries
├── README.md                     # This file
├── Plugin Configuration Guide.md # ⚙️ Detailed plugin setup
│
├── Threat Actors/                # 👤 APT groups, cybercriminals, hacktivists
│   ├── APT1.md                   # Example: Comment Crew (PLA Unit 61398)
│   ├── APT28.md                  # Example: Fancy Bear (GRU)
│   ├── APT41.md                  # Example: Winnti/Double Dragon
│   └── Lazarus Group.md          # Example: NK RGB (Bluenoroff/Andariel)
│
├── Malware/                      # 🦠 Malware families, RATs, ransomware
│   ├── PlugX.md                  # Example: Chinese APT RAT
│   ├── X-Agent.md                # Example: APT28 cross-platform RAT
│   └── Cobalt Strike.md          # Example: C2 framework (dual-use)
│
├── Campaigns/                    # ⚔️ Operations, intrusions, attacks
│   ├── SolarWinds Supply Chain Attack.md
│   └── WannaCry Ransomware 2017.md
│
├── Vulnerabilities/              # 🔓 CVEs, exploits, patches
│   └── CVE-2021-44228.md         # Example: Log4Shell
│
├── Incidents/                    # 🚨 Internal incident response
│
├── Reports/                      # 📊 Finished intelligence products
│
├── IOCs/                         # 🔍 Indicator collections
│   └── APT1 IOCs.md              # Example: Structured IOCs
│
├── TTPs/                         # ⚙️ MITRE ATT&CK techniques
│   └── T1566.001.md              # Example: Spearphishing Attachment
│
├── Tools/                        # 🛠️ Offensive/defensive tools
│   └── Mimikatz.md               # Example: Credential theft
│
├── References/                   # 📚 Source documents, reports
│   └── Mandiant APT1 Report.md   # Example: Primary source
│
├── Templates/                    # 📝 Note templates
│   ├── Threat Actor Template.md
│   ├── Malware Template.md
│   ├── Campaign Template.md
│   ├── Vulnerability Template.md
│   ├── Incident Template.md
│   ├── Report Template.md
│   ├── IOC Template.md
│   ├── TTP Template.md
│   ├── Tool Template.md
│   ├── Reference Template.md
│   └── Excalidraw Template.excalidraw.md
│
├── Attachments/                  # 🖼️ Auto-organized images (Paste Image Rename)
│
├── Canvas/                       # 🎨 Visual canvases
│   └── SolarWinds Attack Chain.canvas
│
└── Excalidraw/                   # ✏️ Hand-drawn diagrams + MarkMind
```

---

## 📝 Creating New Notes

### Using Templates
1. **Ctrl+N** (or Cmd+N) → Select template from dropdown
2. Or: Right-click folder → "New note from template"
3. Fill in frontmatter and sections

### Template Variables (Auto-filled)
| Variable | Expands To |
|----------|------------|
| `{{title}}` | File name |
| `{{date:YYYY-MM-DD}}` | Current date |
| `{{date:HH:mm}}` | Current time |

### Linking Best Practices
- **Always use `[[Wikilinks]]`** for internal references
- Link threat actors to their malware/campaigns/IOCs
- Link campaigns to threat actors, malware, tools, TTPs
- Link IOCs to their parent entity
- Use tags: `#threat-actor` `#malware` `#campaign` `#apt` `#china` `#russia` etc.

---

## 🔍 Key Workflows

### 1. Threat Actor Profiling
```
1. Create from "Threat Actor Template"
2. Fill: Overview, Goals, Targeting, TTPs (MITRE table)
3. Link: Malware used, Campaigns, Tools, IOCs
4. Add: References with reliability ratings
5. Visualize: Graph View → Filter #threat-actor
```

### 2. Malware Analysis
```
1. Create from "Malware Template"
2. Document: Capabilities, IOCs, YARA/Sigma rules
3. Link: Threat actors using it, Campaigns
4. Add: Detection rules, Mitigations
5. Track: Variants/versions table
```

### 3. Campaign Mapping
```
1. Create from "Campaign Template"
2. Build: Attack chain table (MITRE tactics)
3. Link: All entities (actors, malware, tools, vulns)
4. Create: Excalidraw attack chain diagram
5. Add: Timeline, Impact assessment
```

### 4. Vulnerability Tracking
```
1. Create from "Vulnerability Template"
2. Track: Affected assets, exploitation status
3. Link: Threat actors exploiting, Malware using it
4. Add: Detection rules, Mitigations, Patch status
5. Query: Dataview for CVSS ≥ 9.0
```

### 5. Incident Response
```
1. Create from "Incident Template"
2. Build: Timeline table (Detection → Recovery)
3. Document: IOCs, TTPs, Attribution
4. Link: Related threat actors, malware, campaigns
5. Add: Lessons learned, Action items
```

### 6. IOC Management
```
1. Create from "IOC Template"
2. Structure: File, Network, Host, Email indicators
3. Add: Detection rules (YARA, Sigma, Snort)
4. Export: STIX, MISP, CSV, JSON
5. Link: Parent entity (actor/campaign/malware)
```

### 7. Intelligence Reporting
```
1. Create from "Report Template"
2. Write: Executive summary, Key findings
3. Include: Dataview tables (auto-updating)
4. Add: Recommendations (Immediate/Short/Long-term)
5. Track: Distribution list, Classification (TLP)
```

---

## 📊 Dataview Queries

The [[CTI/CTI Dashboard.md]] includes live queries for:

| Dashboard Section | Purpose |
|-------------------|---------|
| Quick Navigation | Counts per category with links |
| Threat Actor by Type | Pie chart of APT/Crime/Hacktivist |
| Top 10 Actors by Campaigns | Most active threat actors |
| Malware by Type | RAT/Trojan/Ransomware breakdown |
| Campaign Timeline | Recent campaigns with dates |
| Critical Vulnerabilities | CVSS ≥ 9.0 with exploit status |
| Incident Status | Open/Contained/Closed counts |
| IOC Collections | Recent IOC sets |
| TTP Coverage | MITRE tactic coverage |
| Recent Updates | Notes modified in last 7 days |

### Custom Queries
```dataview
# Find all malware used by APT1
TABLE type, platform
FROM "CTI/Malware"
WHERE contains(threat_actors, "[[CTI/Threat Actors/APT1]]")

# Campaigns in 2024
TABLE threat_actors, start_date, status
FROM "CTI/Campaigns"
WHERE start_date >= "2024-01-01"
SORT start_date DESC
```

---

## 🎨 Visual Analysis

### Graph View (Ctrl+G)
- **Groups:** Color by folder (see Plugin Config Guide)
- **Filters:** Tags `#threat-actor` `#malware` `#campaign`
- **Remove Orphans:** ✅
- **Save Layout:** Ctrl+Alt+S (Persistent Graph)

### Excalidraw Diagrams
- **Attack Chains:** MITRE tactic flow
- **Infrastructure Maps:** C2, redirectors, victims
- **Actor Relationships:** Shared tools, infrastructure
- **Templates:** Use `Excalidraw Template.excalidraw.md`

### MarkMind Mind Maps
- **Campaign Analysis:** Center = Campaign, branches = phases
- **Threat Modeling:** Asset → Threat → Vuln → Control
- **Actor Ecosystem:** Center = Group, branches = subunits

### Canvas
- **Investigation Boards:** Link notes, add text, images
- **Threat Landscapes:** Visual overview
- **Example:** `CTI/Canvas/SolarWinds Attack Chain.canvas`

---

## 🔄 Maintenance

| Task | Frequency | Command/Action |
|------|-----------|----------------|
| Rebuild Dataview Index | Weekly | `Dataview: Rebuild Index` |
| Update Plugins | Monthly | Settings → Community Plugins → Check |
| Save Graph Layout | After changes | Ctrl+Alt+S |
| Clean Attachments | Quarterly | Review `CTI/Attachments/` |
| Review Templates | As needed | Update with new fields |
| Export IOCs | Per engagement | Use IOC Template export formats |

---

## 📚 Methodology References

- **Primary:** [TΞLΞMΞTRY - Mastering CTI with Obsidian](https://github.com/t3l3m3try/Obsidian_Templates)
- **MITRE ATT&CK:** https://attack.mitre.org/
- **STIX/TAXII:** https://oasis-open.github.io/cti-documentation/
- **MISP:** https://www.misp-project.org/
- **FIRST Standards:** https://www.first.org/standards/

---

## 🤝 Contributing

This is your private CTI vault. Customize:
1. **Add organization-specific templates**
2. **Create sector-specific threat actor profiles**
3. **Build custom Dataview dashboards**
4. **Integrate with your SIEM/TIP via export scripts**
5. **Share via Git (encrypted) or Obsidian Sync**

---

## ⚠️ Security Notes

- **Local-first:** No cloud sync unless you enable it
- **Encrypt vault:** Use VeraCrypt/APFS encryption for sensitive data
- **TLP Marking:** Use `classification` frontmatter (TLP:CLEAR/GREEN/AMBER/RED)
- **Access Control:** File system permissions + Obsidian app lock
- **Backup:** Regular encrypted backups of entire vault

---

## 📄 License

This structure is based on TΞLΞMΞTRY's open methodology. Templates and examples are for educational/operational use.

---

*Built with ❤️ for CTI Analysts*
*Last updated: 2024-12-15*