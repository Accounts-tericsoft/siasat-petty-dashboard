# Siasat Petty Cash Dashboard

Interactive single-page dashboard over the **siasat petty** Google Sheet (petty-cash
ledger kept by the Siasat office and MJ), Jan–Sep 2026 — 3,563 transactions, ₹37.9 L.

Open `index.html` in any browser. No build step; Chart.js via CDN. All 3,563 rows and
the monthly cash figures are embedded in the file.

## Filters (top bar)

- **Month** — click any set of month chips (none = all)
- **Category** — multi-select dropdown (11 canonical categories)
- **Type** — recurring / dynamic / untagged (the Occurrence tag exists only from Aug 2026)
- **Search** — matches payee or purpose text
- **Reset** — clears everything

Every KPI, chart, the transaction table and the audit-flag counts recompute live on each filter change.

## KPI box

| Card | Meaning |
|---|---|
| Total spend | Sum of the filtered entries |
| Transactions | Count of filtered entries |
| Cash inflows | First selected month's opening balance + deposits over the selected months |
| Opening → Closing | Cash-in-hand at the start and end of the selected month range |
| Audit flags | Flagged entries in the filtered set (see below) |

Each numeric card carries a 9-month sparkline (selected months dotted). When exactly one
month is selected, the first three cards also show a **% vs previous month**.

## Insights panel

Selecting a single month shows an auto-generated **month vs previous-month** comparison:
spend and entry-count change, biggest category rise and drop, the payee that grew most,
the largest single entry, the closing-cash change and whether deposits covered spend,
recurring vs one-off split (where tagged), and the audit-flag change. It respects any
active category / type / search filter.

## Charts

Monthly cash movement (ledger spend, filtered spend, deposits, closing-balance line) ·
category mix (donut + horizontal bar) · daily spend line · top payees (name-normalised).

## Audit flags

An entry is flagged if any of: amount ≥ ₹10,000 (large cash) · category is Salary or
Charity and amount ≥ ₹5,000 (should be a bank transfer) · it is a likely duplicate
(same month + date + payee + purpose + amount, counted from the 2nd occurrence).

## Data integrity

Every month reconciles: `opening + deposits − spend = closing`, and each month's closing
equals the next month's opening. The Jan–Aug ledger total (₹37,81,263) matches the sheet's
own monthly "Spends" figures.

*Internal — Tericsoft / Siasat accounts.*
