<div align="center">

<br/>

# STEWRD Heritage Copilot

### A management copilot for non-professional heritage custodians

[![GitHub Pages](https://img.shields.io/badge/Try%20it-GitHub%20Pages-5c6a2b?style=flat-square)](https://mightytonylun.github.io/stewrd-heritage-copilot/)&nbsp;
[![Release](https://img.shields.io/github/v/release/mightytonylun/stewrd-heritage-copilot?style=flat-square&color=8b3a2f&label=Release)](https://github.com/mightytonylun/stewrd-heritage-copilot/releases)&nbsp;
![Status](https://img.shields.io/badge/Status-Early%20access-c0a882?style=flat-square)

**[mightytonylun.github.io/stewrd-heritage-copilot →](https://mightytonylun.github.io/stewrd-heritage-copilot/)**

[See the Waller House demo](https://mightytonylun.github.io/stewrd-heritage-copilot/demo/) · [Try the tools](https://mightytonylun.github.io/stewrd-heritage-copilot/#) · [Skill pack (Agent 0)](https://github.com/mightytonylun/heritage-copilot-skill)

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

## See it working: the Waller House demo

**[Open the demo →](https://mightytonylun.github.io/stewrd-heritage-copilot/demo/)** · [phone version](https://mightytonylun.github.io/stewrd-heritage-copilot/demo/phone.html)

One full check-up of Napier Waller House (Ivanhoe, Melbourne): the walk-round prompts, recording each element, the priority list, and the care plan, with all the agents working together. It shows where STEWRD is heading and works on a laptop or a phone.

*Defects, works and photos come from the National Trust of Australia (Victoria) Property Condition Report 2026. That report gives no condition grades, so the grades and priorities in the demo are illustrative, and assessor results in the demo were prepared in advance rather than run live.*

---

## Agents

| | Agent | What it does | |
|--|-------|-------------|--|
| **A0** | **Heritage Document Analyser** | Reads a place's CMPs, condition reports and significance statements, and drafts a plain-English Place Brief plus the walk-round prompts for each check-up. Set up once, by a professional. | [Skill →](https://github.com/mightytonylun/heritage-copilot-skill) |
| **A1** | **Condition Assessor** | Photograph a building element → AI rates it Good / Fair / Poor / Critical → plain-English next step. Works on phone, 5 AI providers, API key remembered. | [Open →](https://mightytonylun.github.io/stewrd-heritage-copilot/agent-1/) |
| **A2** | **Condition Report Digitizer** | Guided 10-section on-site form for structured condition recording. Session save/restore, offline-capable, exports to text. | [Open →](https://mightytonylun.github.io/stewrd-heritage-copilot/agent-2/) |
| **A3** | **Maintenance Planner** | Prioritises repair schedule from A1 and A2 output — ranked by urgency, cost tier, and consequence of inaction. | Planned · [in the demo](https://mightytonylun.github.io/stewrd-heritage-copilot/demo/) |
| **A4** | **Archive Organiser** | Structures accumulated assessment data into a discoverable, publishable archive. | Planned |

*Agent 0 runs today as `heritage-brief`, part of the open [heritage-copilot skill pack](https://github.com/mightytonylun/heritage-copilot-skill) for Claude. Bringing it inside the app is planned.*

---

## Condition levels (Agent 1)

Built from ICOMOS condition state definitions and Heritage Victoria guidelines:

| | Level | Headline | Who acts |
|--|-------|----------|---------|
| 🟢 | **Good** | Stable | No action needed |
| 🟡 | **Fair** | Monitor | Owner or standard tradesperson |
| 🟠 | **Poor** | Engage a tradesperson | Heritage tradesperson within 3–6 months |
| 🔴 | **Critical** | Refer to a specialist | Urgent — do not DIY |

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

**On iPhone / Android:** Agent 1 has a "Take photo" button that opens the rear camera directly. Agent 2 is tablet-optimised. The demo works on phones too.

---

## Early access

We're sharing these tools as they're built and want feedback from real custodians. Try them on your property — [open an issue](https://github.com/mightytonylun/stewrd-heritage-copilot/issues) with what you find.

---
