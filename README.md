# Heritage Condition Report Copilot

[![License: Proprietary](https://img.shields.io/badge/License-Proprietary-red.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0-blue.svg)](https://github.com/mightytonylun/heritage-condition-report-copilot/releases)
[![Browser Support](https://img.shields.io/badge/browser-all%20modern-brightgreen.svg)](#browser-support)

> Desktop webapp that works alongside Microsoft Word for heritage property assessments. v1.0: Desktop copilot for structured documentation and Word export. v1.1+: Mobile field capture with camera integration.

## Overview

Heritage Condition Report Copilot v1.0 is a **desktop companion tool** that runs in your browser alongside Word documents. Inspectors structure their assessment findings, attach photos, group defects by element, and export formatted tables directly to Word reports—no setup required, all data stored locally.

**v1.0 Workflow:**
```
📋 Browser form open → Document findings → Export to Word → Finalize report
```

**Perfect for:**
- Heritage conservationists documenting property conditions
- Structural engineers preparing condition reports
- Insurance assessors creating assessment documents
- Maintenance planners estimating repair costs

**v1.1+ will add:** Direct tablet camera capture for on-site photo documentation.

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [How It Works](#how-it-works)
- [Data Structure](#data-structure)
- [Browser Support](#browser-support)
- [Troubleshooting](#troubleshooting)
- [Roadmap](#roadmap)
- [License](#license)

## Features

### Core Functionality
- **Structured Assessment Sections** — Electrical, plumbing, structural, hazard identification, and more
- **Grouped Entry System** — Organize findings by reference numbers + room/element categories
- **Photo Support** — Attach images directly to entries; stored locally in browser
- **Cost Estimation** — Calculate subtotals by defect group for budget planning
- **Word Export** — Copy formatted tables directly into condition report documents
- **Offline-First** — All data persists in-browser; works without internet
- **Desktop-Optimized** — Built for work alongside Word (responsive design for future mobile capture)

### User Experience
- **Zero Setup** — Open HTML file, start using immediately
- **Auto-Save** — Data persists as you type (browser localStorage)
- **Sample Data** — Pre-populated examples demonstrate structure and workflow
- **Inline Editing** — Modify entries directly in preview tables
- **Clear/Reset** — Easily clear all data to start fresh

## Quick Start

### Opening the Tool

```bash
# Option 1: Direct download
# Download heritage-property-assessment.html and open in your browser

# Option 2: Clone repository
git clone https://github.com/mightytonylun/heritage-condition-report-copilot.git
cd heritage-condition-report-copilot
# Open heritage-property-assessment.html in your browser
```

### First Use (Desktop)

1. **Open** `heritage-property-assessment.html` in desktop browser
2. **Open Word document** in parallel for your condition report
3. **Review** sample data to understand structure (then clear for your property)
4. **Document** findings in form sections
5. **Export to Word** using copy buttons to transfer data to your report

### v1.0 Desktop Workflow Example

```
Browser + Word open  → Document conditions and findings in form
↓
Structured entry     → Organize defects by element/room with ref numbers
↓
Export to Word       → Copy grouped tables into condition report
↓
Final report         → Format and finalize for submission/archive
```

### Future: v1.1 Field Workflow (Mobile Camera)

Coming in v1.1: Capture photos directly on tablets on-site using device camera, then sync with desktop for reporting.

## How It Works

### Assessment Sections

The form is organized into 10 logical sections:

| Section | Purpose | Grouped? |
|---------|---------|----------|
| **1. Property Details** | Address, date, inspector | No |
| **2. Electrical** | RCD presence, condition notes | No |
| **3. Plumbing** | Leaks, pressure, condition | No |
| **4. Moisture/Ventilation** | Dampness, condensation, hazards | No |
| **5. Hazardous Materials** | Asbestos, lead, other | No |
| **6. Structural** | Foundation, walls, movement | No |
| **7. Exterior Elements** | Roof, elevations, etc. | ✓ By location |
| **8. Interior Spaces** | Rooms, finishes, condition | ✓ By room |
| **9. Defects** | Issues, priority, repairs | ✓ By element |
| **10. Overall Summary** | Final assessment notes | No |

### Grouped Entry System (Sections 7, 8, 9)

For Exterior, Interior, and Defects sections, structure entries with:

- **Reference Number** — Unique identifier (e.g., `RM-01`, `R-01`, `D-02`)
- **Room/Element/Location** — Grouping category (e.g., `Kitchen`, `Roof`, `Window`)
- **Description** — Detailed notes
- **Priority** — (Defects only) `Urgent`, `Important`, `Routine`
- **Suggested Work** — (Defects only) Recommended repairs
- **Photos** — Attachable evidence images

**Example entry:**
```
Ref Number:  D-01
Element:     Roof
Notes:       Missing tiles on east side, exposed underlayment
Priority:    Urgent
Repair:      Replace tiles, inspect flashing
Photos:      [roof-east-01.jpg, roof-east-02.jpg]
```

### Data Storage

```
┌─────────────────────────┐
│   Browser LocalStorage  │
├─────────────────────────┤
│ • assessmentForm        │  (Sections 1-10)
│ • complexData           │  (Grouped entries 7-9)
│ • assessmentPhotos      │  (Photo data)
└─────────────────────────┘
```

**Privacy & Security:**
- All data stored locally on your device
- No cloud upload or external server
- Private until you choose to export
- Persists across browser sessions

## Browser Support

**v1.0 (Desktop-Optimized)**

| Browser | Support |
|---------|---------|
| **Chrome** | ✓ Full support |
| **Firefox** | ✓ Full support |
| **Safari** | ✓ Full support |
| **Edge** | ✓ Full support |

v1.0 is optimized for desktop and laptop use. Mobile/tablet support improves in v1.1 with camera integration.

**Requirements:**
- Modern JavaScript support (ES6+)
- localStorage enabled
- File upload capability

## Troubleshooting

### Photos not displaying in tables

**Symptom:** Broken image icons in preview tables  
**Solutions:**
- Refresh browser (F5 or Cmd+R)
- Check browser console (F12) for errors
- Ensure browser allows file uploads
- Try a different browser

### Data disappeared after refresh

**Symptom:** Form is empty after closing/reopening  
**Solutions:**
- Check browser privacy settings (may block localStorage)
- Verify browser isn't in private/incognito mode
- Try a standard browsing window
- Keep backups of exported Word documents

### Export to Word not working

**Symptom:** Copy buttons don't transfer data to Word  
**Solutions:**
- Ensure Microsoft Word or compatible software is installed
- Try copying text manually to a new Word document
- Check browser console (F12) for JavaScript errors
- Use browser's developer tools to verify data exists

### Browser console shows storage warnings

**Symptom:** "Tracking Prevention blocked access to storage"  
**Solution:**
- Adjust browser privacy settings to allow storage for this site
- Or use a standard browsing window (not private/incognito mode)

## Tips for Best Results

### Desktop Workflow (v1.0)
- **Dual monitor setup**: One screen for form, one for Word document
- **Copy-paste workflow**: Use export buttons to move data to Word seamlessly
- **Sample data**: Review examples, then clear and document your property
- **Photo uploads**: Pre-collect photos before entering in form, or upload as you document

### Best Practices
- Develop consistent ref number scheme (e.g., `RM-##` for rooms, `D-##` for defects)
- Use element names matching building terminology
- Include timestamps in notes for dated assessments
- Organize photos with descriptive file names before upload

### Future: Mobile Field Work (v1.1+)
- Planned: Direct camera capture on tablets for on-site documentation
- Planned: Sync photos with desktop for reporting

## Roadmap

### v1.0 (Current)
- ✅ Desktop webapp copilot for Word
- ✅ Structured assessment sections
- ✅ Grouped defect entry system
- ✅ Photo attachment and preview
- ✅ Cost estimation and export
- ✅ Offline data persistence

### v1.1 (Planned)
- 📱 Direct camera capture on tablets
- 📱 Mobile-optimized photo workflow
- 🔄 Data sync between devices
- 📊 Enhanced photo gallery
- 🏷️ Photo tagging and organization

### Future Considerations
- PWA installation (app icon on home screen)
- Collaborative editing/sharing
- Cloud backup option
- Template customization
- Advanced reporting features

[View Full Roadmap](https://github.com/mightytonylun/heritage-condition-report-copilot/discussions)

## License

**Proprietary License** — All rights reserved.

This tool is proprietary research and is protected by copyright. See [LICENSE](LICENSE) file for full details.

**You may:**
- ✓ View the source code
- ✓ Use for evaluation and feedback
- ✓ Suggest improvements

**You may not:**
- ✗ Copy, fork, or redistribute
- ✗ Modify or create derivative works
- ✗ Use for commercial purposes without permission

**Collaboration:** For licensing inquiries or collaboration opportunities, please open an issue on the repository.

## Contributing

Found a bug? Have a feature suggestion? Issues and pull requests welcome!

[Report an Issue](https://github.com/mightytonylun/heritage-condition-report-copilot/issues) · [Suggest a Feature](https://github.com/mightytonylun/heritage-condition-report-copilot/issues)

---

**Made for heritage property professionals** who need practical, offline-first assessment tools.

[⬆ Back to top](#heritage-condition-report-copilot)
