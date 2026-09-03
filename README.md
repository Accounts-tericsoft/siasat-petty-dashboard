# Siasat Petty Cash Dashboard

Interactive single-page dashboard over the **siasat petty** Google Sheet (petty-cash
ledger kept by the Siasat office and MJ), Jan–Sep 2026 — 3,563 transactions, ₹37.9 L.

Open `index.html` in any browser. No build step; Chart.js via CDN. All 3,563 rows and
the monthly cash figures (opening / deposits / spend / closing) are embedded in the file.

## Filters (top bar)

- **Month** — click any set of month chips (none = all)
- **Category** — multi-select dropdown (11 canonical categories)
- **Type** — recurring / dynamic / untagged (the Occurrence tag exists only from Aug 2026)
- **Search** — matches payee or purpose text
- **Reset** — clears everything

Every KPI, chart, table and finding recomputes live on each filter change.

## KPI strip

| Card | Meaning |
|---|---|
| Total spend | Sum of the filtered entries |
| Transactions | Count of filtered entries |
| Cash inflows | First selected month's opening balance + deposits over the selected months |
| Opening → Closing | Cash in hand at the start and end of the selected month range |

Each numeric card carries a 9-month sparkline (selected months dotted). With exactly one
month selected, the first three cards also show a **% vs previous month**.

## Insights panel

Selecting a single month shows an auto-generated **month vs previous-month** comparison:
spend and entry-count change, biggest category rise and drop, the payee that grew most,
the largest single entry, the closing-cash change and whether deposits covered spend, and
the recurring vs one-off split (where tagged). Respects the category / type / search filter.

## Charts

Monthly cash movement (ledger spend, filtered spend, deposits, closing-balance line) ·
category mix donut · **spend by category** (single-month view overlays the previous month
and labels each category with its rise/fall %) · daily spend line · top payees.

## Month-by-month breakdown

A category × month matrix (Jan–Sep + Total) with a Total-spend row and
Opening / Deposits / Ledger-spend / Closing cash rows. Follows the category / type / search
filter, always shows every month, highlights the selected month's column.

## Key findings

A data-driven summary computed from the current filter: category concentration, Salary and
Charity routed through cash, large-cash-payment count and total, recurring vs one-off split,
the spend step-down (or single-month vs previous), top-payee share, entry-size
fragmentation, and the payee name-variant count.

## Payee names

`canonPayee()` collapses spelling variants into one name — e.g. `staff / Staff ps / Staff ts`
→ **Staff**; `choto / chotu` → **Choto**; `Murshid / Murshad` folds into **MA Muqtadir**;
plus Md Fayyaz, Md Imran, Office boy, KVS Kamalakar DIPR, Sambhashiva, Intesar, Shoaib,
Zaheeruddin, Dept of post.

## Export & logo

- **CSV** — a title block (filter, timestamp, entry count, total) followed by
  Date / Payee / Purpose / Category / Amount and a TOTAL row, for the currently
  filtered transactions.
- **PDF** — a self-contained report built with jsPDF + autoTable: title, active
  filter, a summary band, and tables for category breakdown, month totals, top
  payees and every filtered transaction (paginated, with a TOTAL). Falls back to
  the browser print dialog if the libraries fail to load.
- **Logo** — *The Siasat Daily* mark, loaded from `siasat.com`. Drop a local
  `siasat-logo.svg` / `siasat-logo.png` next to `index.html` to override it.


## Data integrity

Every month reconciles: `opening + deposits − spend = closing`, and each month's closing
equals the next month's opening. The Jan–Aug ledger total (₹37,81,263) matches the sheet's
own monthly "Spends" figures.

*Internal — Tericsoft / Siasat accounts.*
