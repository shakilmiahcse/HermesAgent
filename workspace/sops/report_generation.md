# SOP: Report Generation Procedure

## Purpose
Standardize the execution of automated and manual reports (Daily Growth Brief, Lead Intelligence, Weekly Competitor Watch) to ensure consistency, accuracy, and professional output format.

## Generation Workflow

### 1. Data Collection & Extraction
- Trigger active integrations (Playwright for web research, YouTube API, FB Graph API).
- Query current CRM / Student registration logs for stats.
- Note: Do NOT guess or estimate numbers. If an API is offline, report the connection status as "Offline - Retrying" and check cache.

### 2. Prompt Selection
- Navigate to the `prompts/v1/` directory.
- Use the target prompt for the specific report:
  - Daily Growth: `daily_growth_brief.md`
  - Lead Info: `daily_lead_intelligence.md`
  - Competitor Audit: `weekly_positioning.md`

### 3. Template Application
- Load output templates from `templates/report/`:
  - `growth_brief.md`
  - `competitor_report.md`
  - `performance_report.md`
  - `positioning_report.md`
- Ensure structure matches layout elements: Today's Top Pains, Competitor Signals, Content Opportunity, Recommended CTA, Next Actions.

### 4. Output Storage & Versioning
- Save final markdown reports to the corresponding subfolders:
  - Daily: `reports/daily/`
  - Weekly: `reports/weekly/`
  - Monthly: `reports/monthly/`
- Standard naming convention: `yyyy-mm-dd-[report_name].md` (e.g. `2026-07-05-growth-brief.md`).

### 5. Verification Checklist
- Run a check to verify that all links embedded in the report are active and functional.
- Validate that no hardcoded pricing or success rates are fabricated in the summary.
