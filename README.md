# OT Canvas — Unified Asset Management

> A demo SaaS interface for Operational Technology asset management, built around the Purdue Enterprise Reference Architecture. Inventory, firmware tracking, EOL planning, and CVE exposure visibility for industrial control system fleets.

![Status](https://img.shields.io/badge/status-prototype-orange)
![License](https://img.shields.io/badge/license-MIT-blue)
![No build](https://img.shields.io/badge/build-none-success)

## Live demo

🔗 **[View live demo →](https://calmony.github.io/ot-canvas/)**


## What it does

OT Canvas is a single-file UI prototype demonstrating what a vendor-agnostic OT asset management platform could look like for a typical mid-size industrial site. It uses synthetic data representing equipment commonly found in process and discrete manufacturing environments:

- **Rockwell** ControlLogix and CompactLogix PLCs, PanelView Plus HMIs, FactoryTalk View SE, FactoryTalk Historian, Studio 5000
- **Siemens** SIMATIC S7-1500, S7-1200, S7-400 PLCs, TIA Portal
- **Kepware (PTC)** KEPServerEX and ThingWorx Kepware Edge OPC servers
- **Hirschmann** RSP35, RSP25, RS30, MACH1040 industrial switches (HiOS)
- **Hirschmann/Belden** Eagle40 industrial firewalls (HiSecOS)

## Features

| Module | Description |
|---|---|
| **Dashboard** | Live metrics: asset count, online/degraded status, open CVEs, EOL-critical count, firmware out-of-date count, Purdue distribution, vendor breakdown |
| **Asset Inventory** | Searchable table with status, name, type, IP, MAC, vendor, model, firmware, EOL, CVE count, zone, and entry method |
| **Purdue Model** | Hierarchical view L0–L4 with import buttons for upper levels and manual-entry buttons for lower levels |
| **Firmware Manager** | Current vs. latest version comparison with update planning hooks |
| **EOL Tracker** | Sorted by soonest expiration, color-coded risk tiers, migration planning hooks |
| **Vulnerabilities** | CVE exposure per asset with one-click POA&M generation hooks |
| **Import / Scan** | Accepts Nmap XML, Tenable .nessus, Claroty, Dragos exports, generic CSV/XLSX for L2–L4; manual entry form for L0–L1 |
| **Alerts** | Severity-filterable feed with critical/warning/info classification |

## Design philosophy

**Lower Purdue levels (0–1)** — sensors, transmitters, PLCs, RTUs — require manual entry. Active scanning of field devices is unsafe in most plants (timing-sensitive protocols, fragile firmware, regulatory constraints under NIST SP 800-82 Rev 3 and IEC 62443).

**Upper Purdue levels (2–4)** — HMIs, switches, OPC servers, historians, SCADA, firewalls, workstations — support automated import from passive or active scan exports.

## Running locally

It's a single HTML file with no build step. Two options:

**Just open the file:**
```bash
git clone https://github.com/YOUR-USERNAME/ot-canvas.git
cd ot-canvas
open index.html   # macOS
xdg-open index.html   # Linux
start index.html   # Windows
```

**Or serve it with any HTTP server:**
```bash
# Python
python3 -m http.server 8000

# Node
npx serve

# Then visit http://localhost:8000
```

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Source**, select **Deploy from a branch**.
4. Choose `main` branch and `/ (root)` folder. Click **Save**.
5. Wait ~30 seconds. Your site will be live at `https://YOUR-USERNAME.github.io/ot-canvas/`.

A workflow file is included at `.github/workflows/pages.yml` that auto-deploys on push to `main`. You can disable it if you prefer the simpler branch-based deploy above.

## Tech stack

- Plain HTML / CSS / JavaScript — no framework, no build, no dependencies beyond a CDN icon font
- [Tabler Icons](https://tabler.io/icons) (webfont via jsDelivr)
- Auto-adapts to system light/dark mode
- Responsive down to mobile width

## Roadmap (if this were real)

- [ ] Backend (Node/Python/Go) with a real asset database (Postgres + TimescaleDB for state history)
- [ ] Actual Nmap XML / .nessus / vendor export parsers
- [ ] NVD CVE API integration for live vulnerability data
- [ ] Vendor advisory ingestion (Rockwell PSIRT, Siemens ProductCERT, CISA ICS-CERT)
- [ ] Role-based access control with site/zone scoping
- [ ] Audit logging for ICS change control
- [ ] STIG-aware compliance overlays (ASD, Apache, WildFly, Windows Server)
- [ ] Network topology visualization with cross-zone traffic analysis
- [ ] Backup / configuration drift tracking for switches and firewalls
- [ ] Mobile-friendly walk-down view for field validation

## Important notes

⚠️ **All data in this demo is synthetic.** No real asset inventories, IP addresses, MAC addresses, CVE counts, or compliance information is represented. The synthetic data was chosen to resemble what an engineer working in a typical industrial environment would recognize.

⚠️ **This is a UI prototype.** Buttons that look like they perform actions (Add Asset, Plan Update, Generate POA&M) show demo alerts rather than executing real workflows. The intent is to communicate the product vision and information architecture, not to be production-functional.

## License

MIT — see [LICENSE](LICENSE).

## Acknowledgments

Concept developed as a vendor-agnostic alternative to OT asset management platforms like Claroty xDome, Dragos Platform, Nozomi Vantage, Armis Centrix, and Tenable OT Security. None of those vendors are affiliated with or endorse this prototype.
