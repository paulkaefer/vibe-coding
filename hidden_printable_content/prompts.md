# Project: Hidden printable content report

> - **Files:** enrollment-report.html
> - **Dates:** 2026-10-18 (from git)
> - **Defaults:** tool TBD · model TBD
> - **Status:** prototype
> - **Use:** TBD
> - **Reusability:** artifact TBD · prompt pattern TBD
> - **Tags:** single-file-html, data-viz, print-pdf, theming
> - **Takeaway (draft):** Print-only content (banner, repeating footer) can be hidden on screen with CSS; the logo was left as a placeholder rather than imitating official branding.
> - **Story value:** TBD
> - **Surprises:** TBD

# Prompt 1:

generate me a simple, clean/professional-looking HTML report with lorem ipsum text and pretty colors (UST branding, including logo, if possible).  dummy data in pie chart, bar chart, maybe table (like fake enrollment, perhaps?). the page should have some hidden content that is only visible when the page is printed. can be either the footer or elsewhere. I'll let you choose, but feel free to ask clarifying questions

## Output 1:

I made the report as a single HTML file: [enrollment-report.html](enrollment-report.html). The JavaScript passes a syntax check, but I couldn't render the page in the browser pane. I haven't seen the layout or the print preview, so open it and try File → Print (or the "Print / Save PDF" button) to check both.

- **Branding:** UST purple (`#510c76`) with gray and lighter purple tints, and a serif/sans pairing for the headings and body.
- **Logo:** The logo is a placeholder shield with "UST" and a wordmark, not the official logo. I didn't try to recreate it. Replace the `<svg>` in the masthead with the official file.
- **Contents:**
  - Four KPI tiles.
  - A donut chart of enrollment by college.
  - A bar chart of headcount for 2020–2025.
  - A table with undergraduate, graduate, total and year-over-year change.
  - Lorem ipsum text throughout.
  - The charts have hover tooltips and need no external libraries.
- **Print-only content:** A banner at the top says it's a printed copy and the figures are fictional. A confidentiality footer repeats on every printed page with the report number and the print date and time. The on-screen footer and the print button are hidden when printing.
- **Fake data:** The table totals, KPIs and charts all come from one data array in the script, so they stay consistent. Edit that array to change the numbers.

If you want to keep this work, I can move this session to a folder you choose.

