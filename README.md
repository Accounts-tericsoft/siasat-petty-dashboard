# Siasat Petty Cash Dashboard

Single-page dashboard over the **siasat petty** Google Sheet (petty-cash ledger kept by the
Siasat office and MJ), covering **Jan–Sep 2026** — 3,563 entries, ₹37.9 L of spend.

Open `index.html` in any browser. No build step; charts via Chart.js CDN.

## What it shows

| Section | Purpose |
|---|---|
| Headline KPIs | 8-month spend, monthly burn rate, committed vs discretionary, cash in hand |
| Monthly spend | Spend bars + entry-count line; the Q1 → Q2 step-down |
| Where the money goes | Category stack by month + overall donut |
| Recurring vs one-off | Aug/Sep `Occurrence` split + the ~50 standing obligations (₹1.56 L/mo) |
| Daily rhythm | Per-month daily-spend sparklines |
| Top payees / largest entries | Name-normalised vendor totals, 30 biggest line items |
| Data quality | Category spellings to merge, action list for next month |

## Data

Figures are embedded in `index.html` (`const DATA`). Regenerate by re-reading the sheet
tabs `Jan26 … Sep26` and the `comments` tab. All monthly totals reconcile to the
category matrix and to the sheet's own Aug balance (1,38,998 + 2,50,000 − 3,31,122 = 57,876).

*Internal — Tericsoft / Siasat accounts.*
