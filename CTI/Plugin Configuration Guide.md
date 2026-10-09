# Obsidian CTI Plugin Configuration Guide

> **Complete setup for all 6 community plugins mentioned in TΞLΞMΞTRY's article**

---

## 📦 Plugin Installation

1. Open Settings → Community Plugins → Turn off Safe Mode
2. Click "Browse" and search for each plugin
3. Install and Enable each one
4. Configure per instructions below

---

## 1. Dataview 🔍

**Purpose:** Live queries, statistics, dynamic tables over your vault

### Installation
- Search: "Dataview"
- Author: blacksmithgu
- Enable: ✅

### Configuration (Settings → Dataview)
```
✅ Enable JavaScript Queries
✅ Enable Inline Queries
✅ Automatic Index Refresh: 5000ms (5 seconds)
✅ Render Markdown in Tables
✅ Show Query Errors
```

### Key Features for CTI
| Feature | Usage |
|---------|-------|
| **DQL Queries** | `dataview` code blocks for tables/lists |
| **Inline Queries** | `= this.field` in notes |
| **Metadata Index** | Frontmatter fields become queryable |
| **Dashboard** | CTI Dashboard.md uses extensively |

### Example Queries for CTI
```dataview
# Threat Actor Table
TABLE type, origin, status, confidence
FROM "CTI/Threat Actors"
SORT file.name

# Campaign Timeline
TABLE threat_actors, start_date, end_date, status
FROM "CTI/Campaigns"
SORT start_date DESC
```

### API for Scripts (Execute Code Plugin)
```javascript
const pages = dv.pages('"CTI/Threat Actors"')
const actors = pages.map(p => ({
  name: p.file.name,
  type: p.type,
  campaigns: p.campaigns?.length || 0
}))
dv.table(["Name", "Type", "Campaigns"], actors.map(a => [a.name, a.type, a.campaigns]))
```

---

## 2. Excalidraw 🎨

**Purpose:** Hand-drawn style diagrams, attack chains, infrastructure maps

### Installation
- Search: "Excalidraw"
- Author: zamiel
- Enable: ✅

### Configuration (Settings → Excalidraw)
```
✅ Auto-link to Markdown files
✅ Matching prefix: "CTI/"
✅ Default folder: CTI/Excalidraw
✅ Template file: CTI/Templates/Excalidraw Template.excalidraw.md
✅ Embed PDFs as images
✅ Dark mode support
```

### CTI-Specific Setup
Create `CTI/Templates/Excalidraw Template.excalidraw.md`:
```markdown
---
type: excalidraw
tags: [excalidraw, template]
---

# {{title}} - Attack Chain Diagram
```

### Use Cases
- **Attack Chains:** Initial Access → Execution → Persistence → etc.
- **Infrastructure Maps:** C2 servers, redirectors, victim networks
- **Actor Relationships:** Shared tools, infrastructure, campaigns
- **Incident Timelines:** Visual incident response flow

### Integration with Notes
```markdown
# Link to Excalidraw from any note
![[CTI/Excalidraw/APT1 Attack Chain.excalidraw]]

# Embed in note
![[CTI/Excalidraw/APT1 Attack Chain.excalidraw|500]]
```

---

## 3. Iconize 🎯

**Purpose:** Custom icons for folders/files for visual organization

### Installation
- Search: "Iconize"
- Author: Florian Woelki
- Enable: ✅

### Configuration (Settings → Iconize)
```
✅ Enable Iconize
✅ Show in File Explorer
✅ Show in Tabs
✅ Show in Graph View
```

### CTI Icon Scheme
Apply via right-click → "Set Icon" on folders/files:

| Folder/File | Icon | Color | Purpose |
|-------------|------|-------|---------|
| `CTI/` | 🛡️ | Blue | Root |
| `CTI/Threat Actors/` | 👤 | Red | Threat actors |
| `CTI/Threat Actors/*.md` | 🎯 | Red | Individual actors |
| `CTI/Malware/` | 🦠 | Green | Malware families |
| `CTI/Malware/*.md` | 🔬 | Green | Individual malware |
| `CTI/Campaigns/` | ⚔️ | Orange | Campaigns |
| `CTI/Campaigns/*.md` | 📋 | Orange | Individual campaigns |
| `CTI/Vulnerabilities/` | 🔓 | Yellow | Vulnerabilities |
| `CTI/Incidents/` | 🚨 | Red | Incidents |
| `CTI/Reports/` | 📊 | Blue | Reports |
| `CTI/IOCs/` | 🔍 | Purple | IOC collections |
| `CTI/TTPs/` | ⚙️ | Gray | TTPs |
| `CTI/Tools/` | 🛠️ | Teal | Tools |
| `CTI/References/` | 📚 | Brown | References |
| `CTI/Templates/` | 📝 | Gray | Templates |
| `CTI/Canvas/` | 🎨 | Pink | Canvas files |
| `CTI/Excalidraw/` | ✏️ | Pink | Excalidraw files |

### Emoji vs Icons
- **Emoji:** Works everywhere, no config needed
- **Iconize:** Use for custom SVG icons, better Graph View integration

---

## 4. MarkMind 🧠

**Purpose:** Mind maps for campaign analysis, threat modeling

### Installation
- Search: "MarkMind"
- Author: lynchj
- Enable: ✅

### Configuration (Settings → MarkMind)
```
✅ Enable MarkMind
✅ Default folder: CTI/Excalidraw (or CTI/MarkMind)
✅ Auto-save: 30 seconds
✅ Theme: Auto (matches Obsidian theme)
```

### CTI Use Cases
1. **Campaign Analysis:** Central node = Campaign, branches = Phases, Tools, Actors, IOCs
2. **Threat Modeling:** Asset → Threats → Vulnerabilities → Controls
3. **Actor Ecosystem:** Central = APT Group, branches = Sub-units, Tools, Targets
4. **Incident Response:** Incident → Detection → Containment → Eradication → Recovery

### Creating Mind Maps
```
# Create new mind map
1. Right-click in CTI/Excalidraw → "New MarkMind Mindmap"
2. Name: "APT41 Campaign Analysis.mm.md"
3. Central node: "APT41 2020 Campaign"
4. Add branches for each MITRE tactic
```

### Export/Integration
- Export as PNG/SVG for reports
- Embed in notes: `![[CTI/Excalidraw/APT41 Analysis.mm.md]]`
- Link nodes to Obsidian notes: `[[CTI/Malware/ShadowPad]]`

---

## 5. Paste Image Rename 🖼️

**Purpose:** Auto-rename pasted images to match note name

### Installation
- Search: "Paste Image Rename"
- Author: iseong
- Enable: ✅

### Configuration (Settings → Paste Image Rename)
```
✅ Enable auto-rename
✅ Rename pattern: "{{note_name}}_{{index}}"
✅ Default folder: CTI/Attachments
✅ Prompt for name: false (auto)
✅ Use frontmatter title: true
```

### Attachment Folder Setup (Settings → Files & Links)
```
Attachment folder path: CTI/Attachments
Default location for new attachments: In subfolder under folder of current file
```

### Workflow
1. Open threat actor note: `CTI/Threat Actors/APT1.md`
2. Copy screenshot (C2 panel, malware analysis, etc.)
3. Paste in note (Ctrl+V)
4. Auto-saves as: `CTI/Attachments/APT1_1.png`, `APT1_2.png`
5. Links inserted: `![[APT1_1.png]]`

### Benefits
- No more `Pasted image 20240115103045.png`
- Images organized by parent note
- Easy to find all images for a threat actor
- Clean Attachments folder

---

## 6. Persistent Graph 🕸️

**Purpose:** Save/restore Graph View layout across sessions

### Installation
- Search: "Persistent Graph"
- Author: oooo9
- Enable: ✅

### Configuration (Settings → Persistent Graph)
```
✅ Enable Persistent Graph
✅ Auto-save interval: 30 seconds
✅ Save on layout change: true
✅ Restore on load: true
```

### Hotkeys (Settings → Hotkeys)
Search "Persistent Graph" and assign:
```
Save Graph Layout: Ctrl+Alt+S
Restore Graph Layout: Ctrl+Alt+R
Reset Graph Layout: Ctrl+Alt+Shift+R
```

### CTI Graph View Setup
1. Open Graph View (Ctrl+G)
2. **Filters:**
   - Tags: `#threat-actor` `#malware` `#campaign` `#vulnerability`
   - Paths: `CTI/`
   - Remove orphans: ✅
3. **Groups (Colors):**
   - `CTI/Threat Actors` → Red (#ff4444)
   - `CTI/Malware` → Green (#44ff44)
   - `CTI/Campaigns` → Orange (#ffaa00)
   - `CTI/Vulnerabilities` → Yellow (#ffff00)
   - `CTI/Incidents` → Red (#ff0000)
   - `CTI/Reports` → Blue (#4488ff)
   - `CTI/IOCs` → Purple (#aa44ff)
   - `CTI/TTPs` → Gray (#888888)
   - `CTI/Tools` → Teal (#00aaaa)
   - `CTI/References` → Brown (#886644)
4. **Display:**
   - Show tags: ✅
   - Show attachments: ❌
   - Link distance: 2-3
5. **Save Layout:** Ctrl+Alt+S
6. **Verify:** Close/reopen Obsidian → Graph restores

### Pro Tips
- Create multiple saved layouts for different views
- Use "Focus" on a node to see its neighborhood
- Combine with Iconize for visual grouping

---

## 🔧 Additional Recommended Plugins

| Plugin | Purpose | CTI Use Case |
|--------|---------|--------------|
| **Execute Code** | Run Python/JS in notes | Automate IOC enrichment, generate reports |
| **Templater** | Advanced templating | Dynamic templates with scripts |
| **Calendar** | Daily notes | Timeline tracking, daily intel summaries |
| **Kanban** | Board view | Incident tracking, investigation workflow |
| **Mermaid Tools** | Better Mermaid | Enhanced diagrams in notes |
| **Various Complements** | Auto-complete | Faster [[wiki-links]] and #tags |
| **QuickAdd** | Capture workflows | Rapid IOC/indicator entry |
| **Dataview Index** | Performance | Faster queries on large vaults |

---

## ⚙️ Obsidian Core Settings for CTI

### Editor
```
✅ Default new tab: Current tab
✅ Show line numbers
✅ Readable line length: Off (for wide tables)
✅ Spell check: Off (technical terms)
```

### Files & Links
```
✅ Use [[Wikilinks]]
✅ Automatically update internal links
✅ Default location for new notes: Folder of current file
✅ Attachment folder: CTI/Attachments
```

### Appearance
```
✅ Show line numbers in editor
✅ Custom CSS: (optional) CTI-specific styling
```

### Hotkeys (Recommended)
```
New note from template: Ctrl+N
Open CTI Dashboard: Ctrl+Shift+D
Graph View: Ctrl+G
Command Palette: Ctrl+P
Quick Switcher: Ctrl+O
```

---

## 📁 Vault Structure Summary

```
CTI/
├── CTI Dashboard.md              # Main entry point
├── Threat Actors/                # 👤 Red
│   ├── APT1.md
│   ├── APT28.md
│   └── ...
├── Malware/                      # 🦠 Green
│   ├── PlugX.md
│   ├── Cobalt Strike.md
│   └── ...
├── Campaigns/                    # ⚔️ Orange
│   ├── SolarWinds Supply Chain Attack.md
│   └── ...
├── Vulnerabilities/              # 🔓 Yellow
│   └── CVE-2021-44228.md
├── Incidents/                    # 🚨 Red
├── Reports/                      # 📊 Blue
├── IOCs/                         # 🔍 Purple
│   └── APT1 IOCs.md
├── TTPs/                         # ⚙️ Gray
├── Tools/                        # 🛠️ Teal
│   └── Mimikatz.md
├── References/                   # 📚 Brown
│   └── Mandiant APT1 Report.md
├── Templates/                    # 📝 Gray
│   ├── Threat Actor Template.md
│   ├── Malware Template.md
│   ├── Campaign Template.md
│   ├── Vulnerability Template.md
│   ├── Incident Template.md
│   ├── Report Template.md
│   ├── IOC Template.md
│   ├── TTP Template.md
│   ├── Tool Template.md
│   └── Reference Template.md
├── Attachments/                  # Auto-organized images
├── Canvas/                       # 🎨 Canvas files
└── Excalidraw/                   # ✏️ Excalidraw + MarkMind
```

---

## ✅ Verification Checklist

After setup, verify:
- [ ] All 6 plugins installed and enabled
- [ ] Dataview queries in CTI Dashboard render correctly
- [ ] Excalidraw creates/opens drawings in CTI/Excalidraw
- [ ] Iconize shows icons in file explorer
- [ ] MarkMind creates mind maps
- [ ] Paste Image Rename saves to CTI/Attachments with correct naming
- [ ] Persistent Graph saves/restores layout
- [ ] Templates accessible via Ctrl+N → Select Template
- [ ] Graph View shows colored groups, no orphans
- [ ] Links between notes work bidirectionally

---

## 🔄 Maintenance

| Task | Frequency |
|------|-----------|
| Dataview: Rebuild Index | Weekly or after bulk imports |
| Plugin Updates | Monthly |
| Graph Layout Save | After major restructuring |
| Attachment Cleanup | Quarterly |
| Template Updates | As methodology evolves |

---

*Based on TΞLΞMΞTRY's Obsidian CTI Methodology*
*Last updated: 2024-12-15*