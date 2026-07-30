# Bank Loan Analysis Dashboard (Excel)

An interactive Excel dashboard that analyzes a bank's consumer loan portfolio — loan performance, risk (good vs. bad loans), and month-over-month trends — built entirely with native Excel tools (PivotTables, PivotCharts, and slicers).

## What this project does

The workbook takes a raw loan-book export (~37,000+ individual loan records) and turns it into a set of executive-ready dashboards that answer questions like:

- How much has the bank funded, and how much has it collected back?
- What share of the portfolio is "Good" (Fully Paid / Current) vs. "Bad" (Charged Off)?
- How is loan issuance trending month-over-month (MTD vs. PMTD, with MoM % change)?
- How does risk/performance vary by loan grade, term, purpose, state, home ownership, and verification status?

## Workbook structure

| Sheet | Purpose |
|---|---|
| **Data** | Raw source table — one row per loan, ~25 fields (loan amount, interest rate, DTI, term, grade, status, dates, borrower info, etc.) |
| **Design_Sheet** | Analytical engine — all PivotTables (15) and PivotCharts (10) live here, feeding the dashboards. Includes KPI summary blocks (MTD, PMTD, MoM %) and a Good vs. Bad Loan breakdown |
| **SUMMARY DASHBOARD** | Front-facing dashboard with 5 charts summarizing portfolio composition and performance |
| **OVERVIEW DASHBOARD** | Front-facing dashboard with 4 charts (including a trend line and a doughnut chart) plus interactive slicers for filtering |

## Key metrics tracked

- **Total Applications** (loan count)
- **Total Funded Amount** (`Sum of loan_amount`)
- **Total Amount Received** (`Sum of total_payment`)
- **Average Interest Rate**
- **Average DTI (Debt-to-Income ratio)**
- **Good Loan vs. Bad Loan** split (derived field, based on `loan_status`)
- **MTD / PMTD / MoM %** — month-to-date, prior-month-to-date, and month-over-month change for each KPI above

## Techniques used

- **PivotTables** for multi-dimensional aggregation (count, sum, average) across grade, term, purpose, state, and time
- **PivotCharts** for visual summaries (bar charts for categorical comparisons, a line chart for the funding trend, a doughnut chart for portfolio composition)
- **Slicers** for interactive, click-to-filter dashboard exploration
- **Derived/calculated fields** (e.g., Good vs. Bad Loan classification from raw loan status codes)
- **Time-based comparison logic** (MTD vs. PMTD vs. MoM %) to track trend direction, not just point-in-time totals
- **Dashboard design** separating raw data → calculation layer → presentation layer across dedicated sheets, so the dashboards stay clean and reflect the underlying pivots automatically

## How to use it

1. Open the workbook and go to either dashboard sheet.
2. Use the slicers to filter by dimensions like loan grade, term, or purpose.

## Author
Gaurav Singh
4. All charts and KPI cards update automatically since they're driven by PivotTables referencing the `Data` sheet.
5. To refresh with new data: replace/append rows in the `Data` sheet, then right-click any PivotTable → **Refresh All**.
