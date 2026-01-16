# Journal Entry Generator

An AI-powered agent that automatically generates double-entry journal entries from source transactions. Built as a demonstration of accounting workflow automation.

## How It Works

The agent analyzes transactions and applies **accounting rules** to generate proper journal entries:

### Entry Generation Logic

Each transaction is analyzed and classified:

| Transaction Type | Debit Account | Credit Account |
|------------------|---------------|----------------|
| Cash Receipt | Cash | Accounts Receivable / Revenue |
| Operating Expense | Operating Expenses | Cash / Accounts Payable |
| Payroll | Salaries & Wages | Cash |
| Asset Purchase | Fixed Assets | Cash / Accounts Payable |
| Depreciation | Depreciation Expense | Accumulated Depreciation |
| Inventory Purchase | Inventory | Cash / Accounts Payable |
| Deferred Revenue | Cash | Deferred Revenue |
| Revenue Recognition | Deferred Revenue | Service Revenue |
| Accrued Expense | Expense Account | Accrued Liabilities |

### Confidence Levels

| Level | Score | Meaning |
|-------|-------|---------|
| **High** | 95%+ | Clear transaction type, standard entry |
| **Medium** | 80-94% | May need review, some ambiguity |
| **Low** | <80% | Manual review recommended |

## Features

- **Single file upload** - CSV with transaction data
- **Smart classification** - Infers entry type from description and amount
- **Double-entry validation** - Debits always equal credits
- **AI explanations** - Plain-English reasoning for each entry
- **Confidence scoring** - Flags entries needing review
- **Two sample scenarios** - Simple (15 txns) and Complex (25 txns with accruals)

## Usage

1. Open `index.html` in a browser
2. Upload transaction CSV (or click a sample scenario)
3. Click "Generate Journal Entries"
4. Review summary cards for overview
5. Click individual entries to see full details and explanations
6. (Optional) Add OpenAI API key for enhanced AI explanations

## CSV Format

```csv
date,description,amount,type
2024-01-02,Client payment - ABC Corp Invoice #1001,5000,receipt
2024-01-03,Office supplies - Staples,-245.50,expense
2024-01-05,Monthly rent payment,-3500,expense
2024-01-10,Employee payroll - January W1,-12500,payroll
```

### Supported Transaction Types

| Type | Description |
|------|-------------|
| `receipt` | Cash received (positive amount) |
| `expense` | Operating expense (negative amount) |
| `payroll` | Payroll/salary payment |
| `prepaid` | Prepaid expense (e.g., annual insurance) |
| `asset` | Capital asset purchase |
| `deferred` | Deferred revenue received |
| `inventory` | Inventory purchase |
| `accrual` | Accrued expense |
| `depreciation` | Depreciation entry |
| `cogs` | Cost of goods sold |

*Note: If `type` column is missing, the agent will infer type from description and amount.*

## Sample Data

Two scenarios demonstrate the agent's capabilities:

### Simple Scenario
- 15 transactions
- Basic revenue, expenses, payroll
- All high-confidence entries
- Tests standard bookkeeping automation

### Complex Scenario
- 25 transactions
- Includes accruals, deferrals, depreciation, adjustments
- Mix of confidence levels
- Tests handling of month-end accounting

## Technical Details

- Pure HTML/CSS/JavaScript (no build step)
- Runs entirely in browser
- OpenAI API calls made client-side (key never stored)
- Dark theme matching the main Basis Target Map dashboard

## Accounting Principles Applied

- **Double-entry bookkeeping** - Every debit has an equal credit
- **Matching principle** - Expenses matched to revenue periods
- **Revenue recognition** - Revenue recorded when earned
- **Accrual accounting** - Transactions recorded when incurred

## Limitations

- Classification depends on description keywords and amount patterns
- Complex multi-leg entries simplified to two-line format
- Not intended for production use - demonstration only
- Some edge cases may need manual adjustment

---

*Part of the [Basis Target Intelligence Map](../../) project*
