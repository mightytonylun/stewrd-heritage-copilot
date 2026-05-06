# Heritage Condition Report Copilot — Development & Research Log

> A living document tracking the evolution, decisions, and progress of this research project.

---

## Project Overview

**Heritage Condition Report Copilot** is a research-driven tool designed to streamline heritage property assessments. The project evolved from desktop-based reporting needs toward a flexible, field-friendly web application.

**Research Goals:**
- Develop structured assessment methodology for heritage properties
- Create intuitive data capture system for inspectors
- Explore offline-first web technologies for field work
- Test grouped data organization patterns
- Research Word integration workflows

---

## Development Timeline

### Phase 1: Foundation (April 1-7, 2026)
**Focus:** Core assessment form structure

- Created initial form with 10 assessment sections
- Implemented localStorage for offline data persistence
- Added photo attachment capability
- Built Word export functionality
- Created form-minimal-heritage.html as baseline

**Key Decision:** Single HTML file (no build tools) for accessibility and offline capability.

### Phase 2: Enhanced Structure (April 8-10, 2026)
**Focus:** Improving form layouts and data organization

- Developed `form-heritage-copilot-enhanced-updated.html`
- Refined styling and spacing
- Improved section navigation
- Enhanced preview tables
- Tested responsive behavior on different screen sizes

**Key Learning:** Users needed better visual grouping and inline editing.

### Phase 3: Grouped Data Architecture (April 11-13, 2026)
**Focus:** Implementing grouped entry system

**Major Addition:** Reference number + room/element grouping system
- Interior spaces (Section 8): Group by room/location
- Exterior elements (Section 7): Group by location/area
- Defects (Section 9): Group by element with priority/repairs

**Technical Implementation:**
- Changed from simple array to grouped object structure
- Added ref number field (e.g., RM-01, R-01, D-02)
- Implemented cost subtotals by group
- Built grouped preview tables with inline editing

**User Feedback Integrated:**
- Photos now linked to specific entries
- Grouped display reduces visual clutter
- Cost estimation by defect group

### Phase 4: Desktop Copilot Positioning (April 14, 2026)
**Focus:** Clarity on use case and roadmap

**Key Decisions:**
- **v1.0:** Desktop webapp, works alongside Word
  - Structured assessment data entry
  - Grouped defect organization
  - Word export functionality
  - Offline localStorage persistence
  
- **v1.1+:** Mobile field capture (planned)
  - Direct camera access on tablets
  - On-site photo documentation
  - Sync workflow

**Positioning:** Changed from "field-first" to "desktop copilot" to reflect current capabilities accurately.

### Phase 6: UX, Export & Persistence Improvements (April 21, 2026)
**Focus:** v1.1 — addressing feedback on workflow friction and data management

**UX & Workflow:**
- Added **Prev/Next navigation bar** at bottom of every section (no need to use sidebar for linear flow)
- Added **section completion dots** in sidebar (green dot = has data; at-a-glance overview of what's filled)
- Added **Cancel Edit button** when editing a complex entry (previously had to scroll away and lose state)
- Replaced all native `confirm()` dialogs with a polished **custom confirm modal** (consistent with app design)

**Data & Persistence:**
- Added **named multi-assessment sessions** — save, load, delete assessments by name (via Sessions panel in sidebar)
- Sessions auto-persist after each save; current session name shown in sidebar header
- Auto-save is **debounced** (1.2s) to reduce unnecessary localStorage writes during typing
- Save indicator now shows **timestamp** ("Saved 2:34 PM") not just a static "Saved"
- "Clear" now resets session name to "Untitled Assessment"

**Export:**
- No new export format added; prep work done for future improvements

**File:** `heritage-property-assessment-v1.1.html`

---

### Phase 5: Research Protection & Open Source (April 14, 2026)
**Focus:** Licensing and public release

- Released publicly on GitHub: `heritage-condition-report-copilot`
- MIT License with research citation guidelines
- Enables community contributions while protecting research credit
- Clear documentation of features and roadmap

---

### Phase 7: v2 — Tablet-First Rebuild (April 24, 2026)
**Focus:** Full redesign for iPad/tablet field use; structural UX overhaul

**Why v2 (not patching v1.1):**
- v1.1 had an inconsistent layout language: sections 1–6 used entry-left/preview-right, sections 7–9 used preview-top/entry-right — a structural problem, not patchable
- Tablet requirement demanded PWA (`getUserMedia`, manifest, service worker) — justified a clean rebuild
- Opportunity to unify condition rating as the primary input across all 10 sections

**Architecture decisions for v2:**
- **HTML + PWA**: still single-file; PWA manifest + service worker injected at runtime (no server needed)
- **Tablet-first layout**: pill strip nav on mobile/tablet → sidebar collapses on desktop
- **Unified card pattern**: same component for all 10 sections — condition rating + notes + entries
- **Condition rating (Good/Fair/Poor/Critical/N/A)** as primary first-class input on every section
- **getUserMedia camera**: direct camera capture on iPad, falls back to gallery picker on desktop
- **Slide-up entry drawer**: replaces inline form — same UX for all complex entries
- **Auto-suggested ref numbers**: auto-increments per section prefix (EE-01, RM-01, D-01)
- **Entry success toast + row flash**: green toast + highlighted new row on add
- **Single "Export Report" CTA** in header/sidebar; export modal with Word/JSON/CSV/Print

**New in v2 data layer:**
- All localStorage keys namespaced `hcl_v2_*` (no conflict with v1.1)
- `photoData` keyed by `entry.id` (stable across edits)
- Session auto-persist runs only for named sessions (skips "Untitled Assessment")

**File:** `v2/heritage-copilot-v2.html`

---

## Architectural Decisions

### 1. Single HTML File
**Decision:** Entire application in one .html file (no separate CSS/JS files)

**Rationale:**
- ✓ Zero setup/deployment complexity
- ✓ Works offline immediately
- ✓ Easy to share and version
- ✓ Can be used directly without build tools
- ✓ Perfect for field work (no dependencies)

**Trade-off:** File size (146KB), but acceptable for this use case.

### 2. LocalStorage for Data Persistence
**Decision:** Browser localStorage only, no server/cloud

**Rationale:**
- ✓ True offline capability
- ✓ Privacy (data stays on device)
- ✓ No infrastructure costs
- ✓ Simplicity

**Trade-off:** Single device only (v1.1 can add sync).

### 3. Grouped Entry Architecture
**Decision:** Reference number + room/element for organization

**Rationale:**
- ✓ Matches how inspectors think about buildings (by location)
- ✓ Reduces data entry friction (shared location)
- ✓ Enables cost estimation by group
- ✓ Better visual organization in preview

**Example:** `RM-01 Kitchen, RM-02 Kitchen` groups related findings by room.

### 4. Word Export (Not Integration)
**Decision:** Copy/paste tables into Word, not OLE automation

**Rationale:**
- ✓ Works on all platforms (Mac, Windows, Linux)
- ✓ Works with any word processor (Word, Google Docs, LibreOffice)
- ✓ User has full control of final document
- ✓ No dependency on Office APIs

**Trade-off:** Manual copy step instead of automatic push.

### 5. v1.0 as Desktop Tool
**Decision:** Focus v1.0 on desktop use, plan mobile for v1.1

**Rationale:**
- ✓ Can ship stable version now
- ✓ Mobile adds complexity (camera API, touch optimization)
- ✓ Allows iteration based on v1.0 user feedback
- ✓ Honest about current capabilities

**Future:** v1.1 will add tablet/mobile camera capture.

---

## Technical Architecture

### Data Structure
```javascript
// Basic assessment (non-grouped)
formData = {
  1: { address, date, inspector, ... },
  2: { rcdPresent, condition, ... },
  // ... sections 3-10
}

// Grouped complex data
complexData = {
  7: [ // Exterior elements
    { part: "R-01", room: "Roof", notes: "...", photos: [] },
    { part: "EE-01", room: "East Elevation", ... }
  ],
  8: [ // Interior spaces
    { part: "RM-01", room: "Kitchen", ... }
  ],
  9: [ // Defects (with priority/repairs)
    { part: "D-01", room: "Roof", priority: "Urgent", suggestedWork: "...", ... }
  ]
}
```

### Key Functions
- `renderSection()` — Build form sections
- `renderComplexSection()` — Grouped entry forms (7,8,9)
- `updatePreview()` — Grouped table display with grouping logic
- `addComplexEntry()` — Add/validate grouped entries
- `copyTableToWord()` — Export to Word-compatible HTML
- `loadFormData()` — localStorage read with error handling

### Browser APIs Used
- `localStorage` — Data persistence
- `FileReader API` — Photo upload/preview
- `Blob & DataURL` — Photo storage in browser memory
- Standard DOM/CSS — No frameworks

---

## Key Features Implemented

✅ **Structured Assessment**
- 10 logical assessment sections
- Input validation and required fields
- Clear organization by building system

✅ **Grouped Entry System** (New in Phase 3)
- Reference numbers (RM-01, D-02, etc.)
- Room/element/location grouping
- Priority levels for defects
- Suggested work recommendations

✅ **Photo Documentation**
- Attach photos to specific entries
- Photo preview in tables
- Stored locally in browser

✅ **Cost Estimation**
- Per-defect cost entry
- Subtotals by group
- Cost summary section

✅ **Word Export**
- Copy grouped tables to Word
- Formatted for reports
- Includes all entry data

✅ **Offline-First**
- Works without internet
- localStorage persistence
- Error handling for privacy-blocked browsers

✅ **Sample Data**
- Pre-populated examples
- Demonstrates structure and workflow
- Can be cleared to start fresh

---

## Testing & Validation

### Desktop Browsers (v1.0)
- ✅ Chrome (full support)
- ✅ Firefox (full support)
- ✅ Safari (full support)
- ✅ Edge (full support)

### Known Limitations
- ⚠ Mobile photo capture: Not yet (v1.1 feature)
- ⚠ Cloud sync: Not available (local only)
- ⚠ Collaborative editing: Not available

### Future Testing
- v1.1: Tablet camera capture workflow
- Mobile touch optimization
- Sync between devices
- PWA installation (future enhancement)

---

## What's Next (v1.1 & Beyond)

### v1.1 (Planned)
- 📱 Direct camera capture on tablets
- 📱 Mobile-optimized photo workflow
- 🏷️ Photo tagging and organization
- 📊 Enhanced photo gallery

### v1.2+ (Considerations)
- 🔄 Device-to-device sync
- ☁️ Optional cloud backup
- 👥 Collaborative editing
- 📱 PWA installation (app icon)
- 🎨 Template customization
- 📈 Advanced reporting features

### Research Directions
- Patterns in heritage assessment workflows
- Effectiveness of grouped data organization
- Mobile vs. desktop preferences for field work
- Integration patterns with Office documents

---

## Lessons Learned

### Technical
1. **Single-file approach works** — No regrets on this architecture
2. **localStorage is reliable** — With proper error handling
3. **Grouped organization matters** — Reduces cognitive load vs. flat lists
4. **Word export via copy/paste is practical** — Better than trying complex Office APIs

### UX/Design
1. **Reference numbers are essential** — Users think in categories (RM-01, D-02)
2. **Inline editing beats separate forms** — Faster feedback loop
3. **Visual grouping reduces errors** — Related items together
4. **Photo linking improves accuracy** — Evidence directly attached

### Research
1. **Desktop-first makes sense for v1.0** — Stable before adding mobile complexity
2. **Citation/attribution matters** — Clear attribution in MIT license
3. **Open source + research credit works** — Enables collaboration while protecting credit

---

## File Evolution

| File | Phase | Purpose | Status |
|------|-------|---------|--------|
| `form-minimal-heritage.html` | 1 | Baseline form structure | Archived (reference) |
| `form-heritage-copilot-enhanced-updated.html` | 2 | Layout improvements | Archived (reference) |
| `heritage-property-assessment.html` | 3-5 | Production v1.0 | Archived (reference) |
| `heritage-property-assessment-v1.1.html` | 6 | Production v1.1 (desktop copilot) | Archived (reference) |
| `v2/heritage-copilot-v2.html` | 7 | **v2 — Tablet-first PWA rebuild** | Active |

---

## How to Continue Development

### Adding v1.1 Camera Capture
1. Research device camera APIs (getUserMedia)
2. Add photo preview interface for mobile
3. Test on actual tablets (iPad, Android)
4. Optimize touch interactions
5. Test with real field work scenario

### Before Major Changes
1. Create new .html version (document your iteration)
2. Keep old version for reference
3. Test in all browsers
4. Get user feedback before finalizing

### Deployment
- GitHub remains source of truth
- Releases documented as tags
- README updated with new features
- DEVELOPMENT.md updated with learnings

---

## Research Notes

**Citation:** If you use this project in research/publications, please cite:
```
Heritage Condition Report Copilot
https://github.com/mightytonylun/heritage-condition-report-copilot
```

**Research Questions Being Explored:**
- How do digital tools change heritage assessment workflows?
- What data organization patterns best serve field inspectors?
- How effective is offline-first architecture for heritage documentation?
- What role can web technologies play in heritage preservation work?

---

## Contact & Collaboration

For questions, feedback, or collaboration on this research:
- Open an issue on GitHub
- Discuss feature ideas
- Share field testing experiences
- Contribute improvements (with citation)

---

**Last Updated:** 2026-04-24  
**Current Version:** v2.0 (Tablet-First PWA Rebuild)  
**Next Phase:** v2.1 (Field testing, photo annotation, sync)
