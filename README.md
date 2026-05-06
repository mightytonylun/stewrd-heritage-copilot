<div align="center">

<br/>

# STEWRD Heritage Copilot

### A management copilot for non-professional heritage custodians

[![GitHub Pages](https://img.shields.io/badge/Try%20it-GitHub%20Pages-3a6b4a?style=flat-square)](https://mightytonylun.github.io/stewrd-heritage-copilot/)&nbsp;
[![Release](https://img.shields.io/github/v/release/mightytonylun/stewrd-heritage-copilot?style=flat-square&color=8b3a2f&label=Release)](https://github.com/mightytonylun/stewrd-heritage-copilot/releases)&nbsp;
![Status](https://img.shields.io/badge/Status-Early%20access-c0a882?style=flat-square)

**[mightytonylun.github.io/stewrd-heritage-copilot →](https://mightytonylun.github.io/stewrd-heritage-copilot/)**

<br/>

</div>

---

> *"My research is grounded in conservation practice: it addresses a problem I encounter directly in fieldwork — the gap between the knowledge produced by professional conservation and the people who actually look after heritage places day to day."*

---

## The problem

Most small heritage sites have almost nothing to show people. No condition history that reads as a story, no professionally produced archive, no material that makes the place legible to someone who did not already care about it.

The people looking after these places — volunteers running a heritage house a couple of days a week, owner-custodians who inherited a listed property, community groups maintaining a local landmark — know their buildings matter. They just don't know what to do next.

Conservation knowledge stays with professionals. Conservation Management Plans sit in filing cabinets. Every volunteer who takes over starts from scratch. The tools built for the sector assume training, resources, and institutional continuity that most custodians simply don't have.

**STEWRD is a set of tools that bridges that gap.** Not by replacing professionals — but by making expert knowledge persistent and accessible without requiring expertise to receive it.

---

## The framework — NRRT

STEWRD operationalises **NRRT** (Notice, Record, Read, Tend), an everyday care cycle designed for non-specialist custodians:

| Step | What it means |
|------|--------------|
| **Notice** | Routine, attentive observation during regular visits — looking for change, not damage |
| **Record** | Lightweight capture: dated photos and a short plain-English note |
| **Read** | Comparing records across time to detect patterns — where is the place stable, where is it drifting? |
| **Tend** | Small, incremental responses to what the reading reveals — or deliberate, documented non-action |

> *"The most consequential heritage decisions are not the dramatic interventions but the small, repeated acts of attention that either happen or fail to happen between them."*

STEWRD's agents map directly onto this cycle. Each tool handles one part of it.

---

## Agents

| | Agent | What it does | |
|--|-------|-------------|--|
| **A1** | **Condition Assessor** | Photograph a building element → AI rates it Good / Fair / Poor / Critical → plain-English next step. Works on phone, 5 AI providers, API key remembered. | [Open →](https://mightytonylun.github.io/stewrd-heritage-copilot/agent-1/) |
| **A2** | **Condition Report Digitizer** | Guided 10-section on-site form for structured condition recording. Session save/restore, offline-capable, exports to text. | [Open →](https://mightytonylun.github.io/stewrd-heritage-copilot/agent-2/) |
| **A3** | **Urgency Ranker** | Prioritises repair schedule from A1 and A2 output — ranked by urgency, cost tier, and consequence of inaction. | Planned |
| **A4** | **Archive Organiser** | Structures accumulated assessment data into a discoverable, publishable archive. | Planned |
| **A5** | **Narrative Generator** | Transforms pipeline output into accessible narratives — one-page place story, condition summary for grant applications. | Planned |

*Agent 0 (Heritage Document Analyser) is a professional setup layer — ingests existing CMPs, condition reports, and significance statements to create a Property Intelligence Profile that pre-loads all other agents.*

---

## Condition levels (Agent 1)

Built from ICOMOS condition state definitions and Heritage Victoria guidelines:

| | Level | Headline | Who acts |
|--|-------|----------|---------|
| 🟢 | **Good** | Stable — revisit at your next annual check | No action needed |
| 🟡 | **Fair** | Routine upkeep — repaint, clean or seal as needed | Owner or standard tradesperson |
| 🟠 | **Poor** | Consult a heritage professional | Heritage tradesperson within 3–6 months |
| 🔴 | **Critical** | Seek urgent specialist heritage advice | Urgent — do not DIY |

---

## Who this is for

- Volunteer custodians managing heritage houses with no conservation background
- Owner-custodians of heritage-listed properties who need to know what to do next
- Small trusts and committees responsible for community heritage buildings
- Local government officers managing heritage asset portfolios
- Heritage professionals looking for a lightweight tool to leave with non-specialist clients

---

## No installation

Every agent is a single HTML file. Open in any modern browser — no account, no build step, no server.

**On iPhone / Android:** Agent 1 has a "Take photo" button that opens the rear camera directly. Agent 2 is tablet-optimised.

---

## Early access

We're sharing these tools as they're built and want feedback from real custodians. Try them on your property — [open an issue](https://github.com/mightytonylun/stewrd-heritage-copilot/issues) with what you find.

---
