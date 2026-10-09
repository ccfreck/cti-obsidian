# CTI Obsidian Vault

> **A production-ready Cyber Threat Intelligence platform built entirely in Obsidian**

[![Obsidian](https://img.shields.io/badge/Obsidian-1.0+-483699?logo=obsidian&logoColor=white)](https://obsidian.md/)
[![Dataview](https://img.shields.io/badge/Dataview-0.5+-orange)](https://github.com/blacksmithgu/obsidian-dataview)
[![Excalidraw](https://img.shields.io/badge/Excalidraw-2.0+-blue)](https://github.com/zsviczian/obsidian-excalidraw-plugin)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 🎯 What Is This?

This is a **complete, structured CTI (Cyber Threat Intelligence) knowledge base** that transforms [Obsidian](https://obsidian.md/) — a free, local-first note-taking app — into a powerful, searchable, and visual intelligence platform.

**No servers. No subscriptions. No vendor lock-in.** Just Markdown files on your disk, fully under your control.

---

## 🤔 Why This Exists

### The Problem CTI Analysts Face

| Challenge | Traditional Approach | This Vault |
|-----------|---------------------|------------|
| **Data ownership** | Vendor platforms control your data | 100% local, portable Markdown |
| **Context switching** | Multiple tools (TIP, ticketing, docs, chat) | Single unified workspace |
| **Correlation** | Manual, slow, error-prone | Live bidirectional links + Graph View |
| **Visualization** | Static reports, outdated diagrams | Live Graph, Canvas, Excalidraw |
| **Automation** | Expensive SOAR/custom scripts | Dataview queries + Execute Code plugin |
| **Cost** | $50K–$500K+/year for TIPs | **Free** (Obsidian + community plugins) |
| **Offline/Air-gapped** | Rarely supported | Native — runs anywhere |

### The Obsidian Advantage for CTI

> *"Obsidian serves as an ideal CTI platform. It allows you to integrate data from third parties and, most importantly, leverage the intelligence you possess, gathered from incidents/events managed by your company."*
> — **TΞLΞMΞTRY**, [Mastering Cyber Threat Intelligence with Obsidian](https://github.com/t3l3m3try/Obsidian_Templates)

Obsidian's core features map perfectly to CTI workflows:

| Obsidian Feature | CTI Use Case |
|------------------|--------------|
| **[[Wikilinks]]** | Link threat actors → malware → campaigns → IOCs |
| **#Tags** | Filter by #apt #china #ransomware #initial-access |
| **Graph View** | Visualize threat landscape, find hidden connections |
| **Canvas** | Build investigation boards, attack chain diagrams |
| **Templates** | Standardize threat actor profiles, malware analyses |
| **Dataview** | Live dashboards: "Top 10 actors by campaigns" |
| **Excalidraw** | Hand-drawn attack chains, infrastructure maps |
| **Mermaid** | Pie charts, timelines, flow diagrams in notes |
| **Plugins** | Extend with 1000+ community plugins |

---

## 📁 What's Included

```
cti-obsidian/
├── CTI/                          # Main CTI workspace
│   ├── CTI Dashboard.md          # 🏠 Live dashboard with Dataview queries
│   ├── README.md                 # Detailed user guide
│   ├── Plugin Configuration Guide.md
│   │
│   ├── Threat Actors/            # 👤 APT groups, cybercriminals
│   │   ├── APT1.md               # Example: PLA Unit 61398 (Comment Crew)
│   │   ├── APT28.md              # Example: GRU Fancy Bear
│   │   ├── APT41.md              # Example: Winnti/Double Dragon
│   │   └── Lazarus Group.md      # Example: NK RGB
│   │
│   ├── Malware/                  # 🦠 Families, RATs, ransomware
│   │   ├── PlugX.md              # Chinese APT modular RAT
│   │   ├── X-Agent.md            # APT28 cross-platform RAT
│   │   └── Cobalt Strike.md      # C2 framework (dual-use)
│   │
│   ├── Campaigns/                # ⚔️ Operations & intrusions
│   │   ├── SolarWinds Supply Chain Attack.md
│   │   └── WannaCry Ransomware 2017.md
│   │
│   ├── Vulnerabilities/          # 🔓 CVEs with exploit tracking
│   │   └── CVE-2021-44228.md     # Log4Shell
│   │
│   ├── IOCs/                     # 🔍 Structured indicator collections
│   │   └── APT1 IOCs.md          # With YARA, Sigma, STIX export
│   │
│   ├── TTPs/                     # ⚙️ MITRE ATT&CK technique docs
│   │   └── T1566.001.md          # Spearphishing Attachment
│   │
│   ├── Tools/                    # 🛠️ Offensive/defensive tools
│   │   └── Mimikatz.md           # Credential theft
│   │
│   ├── References/               # 📚 Primary sources
│   │   └── Mandiant APT1 Report.md
│   │
│   ├── Templates/                # 📝 10 comprehensive templates
│   │   ├── Threat Actor Template.md
│   │   ├── Malware Template.md
│   │   ├── Campaign Template.md
│   │   ├── Vulnerability Template.md
│   │   ├── Incident Template.md
│   │   ├── Report Template.md
│   │   ├── IOC Template.md
│   │   ├── TTP Template.md
│   │   ├── Tool Template.md
│   │   ├── Reference Template.md
│   │   └── Excalidraw Template.excalidraw.md
│   │
│   ├── Canvas/                   # 🎨 Visual investigation boards
│   │   └── SolarWinds Attack Chain.canvas
│   │
│   ├── Excalidraw/               # ✏️ Hand-drawn diagrams
│   ├── Attachments/              # 🖼️ Auto-organized images
│   ├── Incidents/                # 🚨 Your incident response
│   └── Reports/                  # 📊 Your finished products
│
└── .obsidian/                    # Pre-configured workspace
    ├── community-plugins.json    # All 6 plugins pre-installed
    ├── graph.json                # Color-coded groups
    └── workspace.json            # Saved layout
```

---

## 🚀 Quick Start

### 1. Clone & Open
```bash
git clone https://github.com/ccfreck/cti-obsidian.git
# In Obsidian: File → Open Vault → Select cloned folder
```

### 2. Enable Plugins (one-click)
The vault includes pre-installed plugins. Just enable them:
```
Settings → Community Plugins → Turn off Safe Mode → Enable all
```
| Plugin | Purpose |
|--------|---------|
| **Dataview** | Live queries, dashboards, statistics |
| **Excalidraw** | Attack chains, infrastructure maps |
| **Iconize** | Custom folder/file icons |
| **MarkMind** | Mind maps for campaign analysis |
| **Paste Image Rename** | Auto-organize screenshots |
| **Persistent Graph** | Save/restore Graph View layout |

### 3. Configure Folders
```
Settings → Templates → Template folder: CTI/Templates
Settings → Files & Links → Attachment folder: CTI/Attachments
```

### 4. Start Working
Open `CTI/CTI Dashboard.md` — your command center with live stats.

---

## 💡 Example Workflows

### Create a Threat Actor Profile
1. `Ctrl+N` → Select "Threat Actor Template"
2. Fill frontmatter (type, origin, confidence, tags)
3. Document: Goals, Targeting, TTPs (MITRE table), Malware, Campaigns
4. Link related notes: `[[CTI/Malware/PlugX]]`, `[[CTI/Campaigns/...]]`
5. View in Graph: `Ctrl+G` → Filter `#threat-actor`

### Map a Campaign
1. `Ctrl+N` → Select "Campaign Template"
2. Build attack chain table (MITRE tactics → techniques)
3. Create Excalidraw diagram: Right-click → "New Excalidraw"
4. Link all entities: actors, malware, tools, vulns, IOCs
5. Add timeline, impact assessment, detection opportunities

### Hunt with Dataview
```dataview
# All malware used by APT28
TABLE type, platform
FROM "CTI/Malware"
WHERE contains(threat_actors, "[[CTI/Threat Actors/APT28]]")

# Critical vulns exploited in wild
TABLE cvss_score, exploited, patch_available
FROM "CTI/Vulnerabilities"
WHERE cvss_score >= 9.0 AND exploited = "Yes"
SORT cvss_score DESC
```

### Export IOCs
The IOC Template includes export formats:
- **STIX 2.1** → TIP/SIEM ingestion
- **MISP** → Threat sharing
- **CSV/JSON** → Detection engineering

---

## 🔧 Customization Ideas

| Need | Solution |
|------|----------|
| **Sector-specific** | Add templates for Healthcare/Finance/Energy threats |
| **Team collaboration** | Obsidian Sync / Git / Self-hosted LiveSync |
| **TIP integration** | Execute Code plugin → Push to MISP/OpenCTI |
| **Automated enrichment** | Python in Execute Code → VirusTotal, PassiveTotal APIs |
| **Reporting** | Report Template + Dataview → Auto-updating briefings |
| **Air-gapped** | Runs fully offline; USB transfer only |

---

## 📚 Based On

This implementation follows the methodology from:
- **TΞLΞMΞTRY** — [Mastering Cyber Threat Intelligence with Obsidian](https://github.com/t3l3m3try/Obsidian_Templates)
- **MITRE ATT&CK** — [Attack Framework](https://attack.mitre.org/)
- **STIX/TAXII** — [OASIS CTI Standards](https://oasis-open.github.io/cti-documentation/)

---

## 🤝 Contributing

This is a **personal CTI vault template** — fork and customize for your organization:

1. Fork this repo
2. Add your threat actors, malware, campaigns
3. Build custom Dataview dashboards
4. Create sector-specific templates
5. Share improvements via PR (generic improvements only — no sensitive intel!)

---

## ⚠️ Security Notes

- **Local-first** — No cloud unless you enable Obsidian Sync
- **Encrypt at rest** — Use VeraCrypt/APFS/FileVault for sensitive data
- **TLP Marking** — Use `classification` frontmatter: `TLP:CLEAR/GREEN/AMBER/RED`
- **Access Control** — OS permissions + Obsidian app lock
- **Backup** — Regular encrypted backups of entire vault

---

## 📄 License

MIT License — Free for personal and commercial use.

Templates and methodology credit: **TΞLΞMΞTRY** (CC-BY-SA)

---

## 🙏 Acknowledgments

- **TΞLΞMΞTRY** — Original Obsidian CTI methodology
- **Obsidian Team** — The platform
- **Plugin Authors** — Dataview, Excalidraw, Iconize, MarkMind, Paste Image Rename, Persistent Graph
- **MITRE** — ATT&CK framework
- **CTI Community** — Shared knowledge and standards

---

**Built for CTI analysts, by CTI analysts.** 🛡️