# STEWRD Heritage CareLog

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-2.0--agent2--demo-brightgreen.svg)](https://github.com/mightytonylun/heritage-condition-report-copilot/releases)
[![Browser Support](https://img.shields.io/badge/browser-all%20modern-blue.svg)](#browser-support)

**Agent 2: Condition Report Digitizer** · Part of the STEWRD Heritage Management Copilot

> A free, open-source management copilot for non-professional heritage custodians. Turns a paper-based property walk-around into structured digital data — no specialist knowledge required.

---

## Quick Start

**No installation. No server. No build step.**

1. [Download `heritage-copilot-v2.html`](https://github.com/mightytonylun/heritage-condition-report-copilot/releases/tag/v2.0-agent2-demo) from the latest release
2. Open in any modern browser
3. Click **▶ Load Demo Assessment** to explore a pre-populated example

**iPad / Android Tablet / Phone:** Download using **Chrome or Edge** from the release page — it opens directly in the browser. For PWA installation: Android users tap Menu → Add to Home Screen in Chrome/Edge; iPad/iPhone users must use Safari (Share → Add to Home Screen). Opening a local HTML file in Safari on iOS is not straightforward, so Chrome or Edge is the recommended starting point on all mobile devices.

---

## What Is STEWRD

The heritage conservation sector has a long-tail problem. Well-resourced institutions — national museums, major landmarks, large conservation trusts — are well served. The majority are not:

- Community-managed historic houses run by volunteers
- Small religious buildings maintained by congregations with no conservation budget
- Owner-custodians of heritage-listed homes who inherited both the building and the obligation
- Local government assets managed by generalists with no heritage training

> *"These custodians know their buildings matter. They just don't know what to do next — and every tool built for the sector assumes knowledge and resources they don't have."*

STEWRD is a suite of five modular, free, open-source tools that together give a non-professional custodian the capability to document condition, identify urgency, and generate reports useful to funding bodies and tradespeople.

---

## The Five Agents

```
Agent 2 → Condition Digitizer     ✅ Demo live (this repo)
Agent 1 → AI Photo Assessor       🏗 Next
Agent 3 → Urgency Ranker          📋 Planned
Agent 4 → Archive Organiser       📋 Planned
Agent 5 → Narrative Generator     📋 Planned
```

**Research question for Agent 2:** What is the minimal digital structure for heritage property assessments that a non-expert can reliably complete?

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
- Location / room / element
- Condition rating + notes
- Photo capture (direct camera on tablet, gallery on desktop)
- Priority + estimated cost (defects only)

### Export

| Format | Use |
|--------|-----|
| JSON | Full data backup / pipeline handoff to other STEWRD agents |
| CSV | Entries spreadsheet for cost planning |
| Word / HTML | Copy formatted tables into a condition report document |
| Print / PDF | Browser print dialog |

### Session Management

Save and reload named assessments. Auto-saves every 1.2 seconds. All data stored in `localStorage` — nothing sent anywhere.

---

## Demo Assessment

Click **▶ Load Demo Assessment** in the sidebar to load a pre-populated example:

> **Thornton Cottage** — heritage-listed Victorian worker's cottage, Ballarat VIC 3350  
> Heritage Overlay HO47 · Double brick, bluestone foundations · Terracotta tile roof  
> Assessed by: Sarah Chen, Ballarat Community Heritage Trust

The demo covers all 10 sections including 6 exterior entries, 6 interior rooms, and 8 defects ranging from urgent safety items (electrical rewire, chimney collapse risk) to routine maintenance (repointing, sub-floor vents). Estimated repair cost: ~$21,200.

---

## Architecture

Single `.html` file — no build tools, no dependencies, no server required.

- **CSS:** Custom properties design system, responsive at 900px breakpoint
- **JS:** Vanilla ES6+, no frameworks
- **Storage:** `localStorage` only — all data stays on device
- **PWA:** Manifest + service worker injected as Blob URLs at runtime
- **Camera:** `getUserMedia` with `facingMode: environment` (rear camera on tablets)
- **Export:** Client-side Blob download for JSON/CSV/HTML; browser print for PDF

---

## Browser Support

| Browser | Support |
|---------|---------|
| Chrome | Full |
| Firefox | Full |
| Safari | Full (iOS PWA via Add to Home Screen only) |
| Edge | Full |

Requirements: ES6+, localStorage enabled, camera permissions for photo capture.

---

## Version History

### v2.0 — Agent 2 Demo (April 2026)
- Tablet-first layout with pill-strip navigation
- PWA — Add to Home Screen on iPad
- `getUserMedia` direct camera capture (no file picker on tablet)
- Condition rating (Good / Fair / Poor / Critical / N/A) on every section
- Unified slide-up drawer for grouped entries
- Realistic full demo assessment (Thornton Cottage, Ballarat)
- STEWRD pipeline panel and agent identity
- Deep green `#1B5E38` palette, 7px border radius

### v1.1 (April 2026, archived)
- Desktop sidebar layout
- Gallery photo picker
- Basic export (Word HTML, JSON)

### v1.0 (Initial)
- Desktop copilot for structured documentation alongside Word

---

## Roadmap

### Agent 2 (this tool)
- [ ] Field-tested with real heritage custodians
- [ ] Schema validation and error states
- [ ] Offline sync between devices

### Agent 1 — AI Photo Assessor (next)
- AI-assisted condition classification (Good / Fair / Poor / Critical) from smartphone photos
- Research question: Can automated image analysis of uncontrolled field photos provide condition classifications useful to non-professional custodians?

### Agent 3 — Urgency Ranker (planned)
- Prioritised repair schedule from Agent 2 + Agent 1 output
- Ranking by urgency, cost tier, and consequence of inaction

---

## Citation

```
STEWRD Heritage CareLog — Condition Report Digitizer v2
https://github.com/mightytonylun/heritage-condition-report-copilot
```

## License

MIT License — see [LICENSE](LICENSE) for details.

---

*STEWRD Heritage CareLog · Draft April 2026 · Agent 2 of 5*
