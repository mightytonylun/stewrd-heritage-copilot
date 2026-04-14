# Heritage Condition Report Copilot

A web-based companion tool for heritage property inspectors to document conditions, defects, and maintenance costs while working alongside Word documents.

## Features

- **Field-Friendly Data Entry**: Capture property conditions, structural assessments, and hazard identification in an intuitive form
- **Photo Documentation**: Attach and manage photos for each entry (stored locally in browser)
- **Grouped Entry System**: Organize defects and property elements by:
  - Reference numbers (e.g., RM-01, R-01, D-01)
  - Room/element/location grouping
  - Priority levels and suggested repairs
- **Cost Tracking**: Calculate subtotals by defect group for budget estimation
- **Word Export**: Export findings directly to Word documents for formal reports
- **Offline-Ready**: Data persists in browser localStorage (works without internet)
- **Mobile-Friendly**: Responsive design works on tablets and desktop

## How It Works

### 1. Open & Load Sample Data
Open `heritage-property-assessment.html` in any modern browser. Sample data loads automatically so you can see how it works.

### 2. Fill Out Property Basics
- Property address, inspection date, inspector name
- Electrical, plumbing, structural, and hazard assessments

### 3. Add Grouped Entries
For **Exterior Elements**, **Interior Spaces**, and **Defects**:
- Enter a **Reference Number** (e.g., RM-01, EE-01, D-02)
- Specify the **Room/Element** it belongs to (e.g., Kitchen, Roof, Window)
- Add description, priority, and suggested work
- Attach photos directly from the form

### 4. Review in Preview Tables
View grouped entries organized by room/element, with ref numbers linked to photos.

### 5. Export to Word
Click **Copy to Word** to export findings formatted for your condition report document.

## Sample Data

The form includes sample data demonstrating:
- Interior spaces (Kitchen, Living Room)
- Exterior elements (Roof, East Elevation)
- Defects with priorities (Urgent, Important, Routine)
- Photo attachments and grouped organization

Clear it anytime and start fresh with your own property data.

## Data Storage

- **Browser-Based**: All data saved to your browser's localStorage
- **Private**: Data stays on your device (not sent to any server)
- **Persistent**: Data survives browser refresh (until you clear it)
- **Export**: Copy data to Word documents for reports

## Browser Support

Works on any modern browser (Chrome, Firefox, Safari, Edge) on:
- Desktop computers
- Tablets (iPad, Android tablets)
- Mobile phones (in-browser use)

## Getting Started

1. **Download**: Get `heritage-property-assessment.html`
2. **Open**: Double-click to open in your default browser, or right-click → "Open with" → choose your browser
3. **Use**: Start filling in property details
4. **Export**: Use the "Copy to Word" buttons to generate reports

## Tips for Field Use

- Use on a tablet alongside your inspection checklist
- Photos sync locally as you type
- Internet not required (works offline)
- Data saves automatically as you type
- Export to Word later for final reports

## Workflow Example

1. **Field**: Tablet with form open, capturing photos and entering defect notes
2. **Back at Office**: Open laptop, review entries in the preview tables
3. **Reporting**: Export to Word, format final condition report
4. **Documentation**: Archive Word reports alongside property files

## Troubleshooting

**Photos not showing?**
- Check browser console (F12) for errors
- Ensure browser allows file uploads
- Try refreshing the page

**Data disappeared?**
- Check browser privacy settings aren't blocking localStorage
- Try different browser if problems persist
- Keep backups of exported Word documents

**Export not working?**
- Ensure you have Microsoft Word or compatible software
- Try copying text to new Word document manually
- Check browser console for JavaScript errors

## License

This tool is provided as-is for heritage property assessments and condition reporting.

## Questions or Feedback?

Document issues, suggest features, or share improvements on the project repository.

---

**Version**: 1.0 | **Updated**: 2026-04 | **Format**: Single HTML file (no installation needed)
