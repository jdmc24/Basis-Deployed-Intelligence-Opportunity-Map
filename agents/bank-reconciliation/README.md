# Bank Reconciliation Agent

An AI-powered agent that automatically matches bank statement transactions to book entries and identifies discrepancies. Built as a demonstration of accounting workflow automation.

## How It Works

The agent uses **smart matching** to pair transactions across two data sources:

### Matching Algorithm

Each potential match is scored using multiple signals:

| Signal | Weight | Description |
|--------|--------|-------------|
| Amount | 50 pts | Exact amount match (most reliable) |
| Reference | 30 pts | Matching reference/check numbers |
| Date | 15 pts | Same day or within 3-5 days |
| Description | 10 pts | Common words in vendor names |

Transactions scoring ≥50 points are considered matched.

### Discrepancy Detection

The agent identifies four types of issues:

| Type | Description | Suggested Fix |
|------|-------------|---------------|
| **Missing from Books** | Transaction on bank statement but not recorded | Record the transaction |
| **Missing from Bank** | Recorded in books but not on statement | Verify if cleared or voided |
| **Amount Mismatch** | Same transaction, different amounts | Investigate the difference |
| **Duplicate Entry** | Same transaction recorded multiple times | Remove extra occurrences |

## Features

- **Two-file upload** - Separate bank statement and book entries CSVs
- **Smart matching** - Multi-signal scoring algorithm
- **Summary dashboard** - Transaction counts and financial totals at a glance
- **Drill-down details** - Click any discrepancy for full details
- **AI suggestions** - Optional OpenAI integration for context-aware fix recommendations
- **Two sample scenarios** - Clean (4 issues) and Messy (12+ issues)

## Usage

1. Open `index.html` in a browser
2. Upload bank statement CSV and book entries CSV (or click a sample scenario)
3. Click "Reconcile Transactions"
4. Review summary cards for overview
5. Click individual discrepancies to see details and suggested fixes
6. (Optional) Add OpenAI API key for AI-powered suggestions

## CSV Format

### Bank Statement
```csv
date,description,amount,reference,type
2024-01-02,STRIPE TRANSFER,4250.00,STR-001,deposit
2024-01-03,GUSTO PAYROLL,-3200.00,PAY-001,withdrawal
```

### Book Entries
```csv
date,description,amount,reference,account,category
2024-01-02,Stripe Revenue,4250.00,STR-001,Checking,Revenue
2024-01-03,Gusto - Payroll,-3200.00,PAY-001,Checking,Payroll
```

## Sample Data

Two scenarios demonstrate the agent's capabilities:

### Clean Scenario
- ~25 transactions in each file
- 4 discrepancies to find
- Tests accuracy on well-organized data

### Messy Scenario
- ~35-40 transactions with variations
- 12+ discrepancies including duplicates, mismatches, missing entries
- Tests robustness with real-world messy data

## Technical Details

- Pure HTML/CSS/JavaScript (no build step)
- Runs entirely in browser
- OpenAI API calls made client-side (key never stored)
- Dark theme matching the main Basis Target Map dashboard

## Limitations

- Matching depends on consistent reference numbers or amounts
- Large files (1000+ transactions) may be slow in browser
- Not intended for production use - demonstration only

---

*Part of the [Basis Target Intelligence Map](../../) project*
