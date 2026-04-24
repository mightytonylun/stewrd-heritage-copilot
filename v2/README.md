# STEWRD Heritage CareLog — v2

**Agent 2: Condition Report Digitizer**  
*Part of the STEWRD Heritage Management Copilot*

---

## What Is This

Heritage CareLog v2 is a tablet-first progressive web app (PWA) that turns a heritage property walk-around into structured digital data. It is **Agent 2 of 5** in the STEWRD system — a free, open-source management copilot for non-professional heritage custodians.

A non-expert fills a guided 10-section assessment form covering electrical, plumbing, moisture, hazardous materials, structural, exterior elements, interior spaces, and defects. Output: validated JSON, CSV, and Word-compatible HTML report.

**Research question:** What is the minimal digital structure for heritage property assessments that a non-expert can reliably complete?

---

## How to Open

No installation, no server, no build step required. Everything runs locally — all data is stored in the browser's localStorage, nothing is sent anywhere.

### iPad / iPhone / Android (Recommended)
1. Download `heritage-copilot-v2.html` from the [release page](https://github.com/mightytonylun/heritage-condition-report-copilot/releases/tag/v2.0-agent2-demo) in **Chrome or Edge**
2. The file opens directly in the browser — ready to use immediately

> Safari on iOS does not support opening local HTML files easily. Use Chrome or Edge on all mobile devices.

### Desktop
Open in Chrome, Edge, Firefox, or Safari. The sidebar layout activates automatically at ≥ 900px wide.

---

## Features

### Assessment Structure
10 guided sections covering a complete property condition survey:

| # | Section | Type |
|---|---------|------|
| 1 | Property Details | Form |
| 2 | Electrical | Form + Condition Rating |
| 3 | Plumbing | Form + Condition Rating |
| 4 | Moisture & Ventilation | Form + Condition Rating |
| 5 | Hazardous Materials | Form + Risk Level |
| 6 | Structural | Form + Condition Rating |
| 7 | Exterior Elements | Grouped entries |
| 8 | Interior Spaces | Grouped entries |
| 9 | Defects & Repairs | Defect register with priorities + costs |
| 10 | Overall Summary | Auto-stats + final notes |

### Condition Rating
Every section has a **Good / Fair / Poor / Critical / N/A** rating as the primary input — the core structured data unit that feeds into downstream STEWRD agents.

### Grouped Entry System
Sections 7, 8, and 9 use a slide-up drawer for structured entries:
- Auto-assigned reference numbers (EE-01, RM-01, D-01…)
- Location / room / element field
- Condition rating
- Notes
- Photo capture (camera or gallery)
- Priority + estimated cost (defects only)

### Camera Capture
- **Tablet / phone:** Uses device camera directly via `getUserMedia` — no file picker needed
- **Desktop:** Falls back to gallery file picker
- Multiple photos per entry, thumbnails shown inline

### Session Management
Save and reload named assessments. Auto-saves every 1.2 seconds after input. All data stored in `localStorage` with `hcl_v2_*` namespace (no conflict with v1.x data).

### Export
| Format | Use |
|--------|-----|
| Word / HTML | Copy formatted tables into a condition report document |
| JSON | Full data backup / pipeline handoff to other STEWRD agents |
| CSV | Entries spreadsheet for cost planning |
| Print / PDF | Browser print dialog |

---

## Demo Assessment

Click **▶ Load Demo Assessment** in the sidebar to load a pre-populated example:

> **Thornton Cottage** — heritage-listed Victorian worker's cottage, Ballarat VIC 3350  
> Heritage Overlay HO47 · Double brick, bluestone foundations · Terracotta tile roof  
> Assessed by: Sarah Chen, Ballarat Community Heritage Trust

The demo covers all 10 sections including 6 exterior entries, 6 interior rooms, and 8 defects ranging from urgent safety items (electrical rewire, chimney collapse risk) to routine maintenance (repointing, sub-floor vents). Estimated repair cost: ~$21,200.

This scenario reflects the STEWRD target user — a community trust volunteer with no conservation training managing a property they did not choose.

---

## STEWRD Pipeline

This tool is Agent 2 in a 5-agent system:

```
Agent 2 → Condition Digitizer (this tool) ✅ In progress
Agent 1 → Condition Assessor (AI photo classification) 🏗 Next
Agent 3 → Urgency Ranker (prioritised repair schedule) 📋 Planned
Agent 4 → Archive Organiser (structured dataset) 📋 Planned
Agent 5 → Narrative Generator (stakeholder reports) 📋 Planned
```

The JSON export from this tool is designed to feed directly into Agent 1 (photo condition classification) and Agent 3 (urgency ranking). The `detected_issues`, `condition`, and `confidence` fields from Agent 1 map to the same schema as this tool's defect register entries.

---

## What's New in v2 vs v1.1

| Feature | v1.1 | v2 |
|---------|------|----|
| Layout | Desktop sidebar only | Tablet pill strip + desktop sidebar |
| Condition rating | Not present | Every section, primary input |
| Entry pattern | Inline form per section | Unified slide-up drawer |
| Camera | Gallery picker only | `getUserMedia` (direct camera on tablet) |
| PWA | No | Manifest + service worker (Add to Home Screen) |
| STEWRD branding | None | Pipeline panel, agent identity |
| Demo data | Sample data button | Realistic full-assessment demo |
| Border radius | 16px (soft) | 7px (professional) |
| Primary colour | Warm brown | Deep green `#1B5E38` |
| localStorage namespace | `assessmentForm` etc. | `hcl_v2_*` (no conflict) |

---

## Architecture

Single `.html` file — no build tools, no dependencies, no server required.

- **CSS:** Custom properties design system, responsive at 900px breakpoint
- **JS:** Vanilla ES6+, no frameworks
- **Storage:** `localStorage` only — all data stays on device
- **PWA:** Manifest + service worker injected as Blob URLs at runtime — keeps the file self-contained
- **Camera:** `getUserMedia` with `facingMode: environment` default (rear camera on tablets)
- **Export:** Client-side Blob download for JSON/CSV/HTML; browser print for PDF

---

## File

| File | Description |
|------|-------------|
| `heritage-copilot-v2.html` | Complete application — open directly in browser |
| `README.md` | This file |

---

## Citation

```
STEWRD Heritage CareLog — Condition Report Digitizer v2
https://github.com/mightytonylun/heritage-condition-report-copilot
```

MIT License — see [LICENSE](../LICENSE)

---

*STEWRD Heritage CareLog · Draft April 2026 · Agent 2 of 5*
