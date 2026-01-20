# Journal Entry Generator - Interview Walkthrough

This document provides talking points for demonstrating the Journal Entry Generator agent during an interview.

---

## Opening Statement

> "This agent takes classified transactions and generates proper double-entry journal entries - determining which accounts to debit and credit, and explaining the accounting logic. Every transaction needs a balanced entry, and this automates that process."

---

## Key Demo Points

### 1. The Engine Selector

> "Four processing modes, consistent with the other agents:
>
> - **Rules** ⚡ - Pattern-based account mapping. Fast and consistent.
> - **Hybrid** 🔀 - Rules for standard entries, LLM for complex scenarios.
> - **Ollama** 🦙 - Local LLM testing.
> - **OpenAI** 🤖 - Full LLM-powered account selection with explanations."

### 2. Double-Entry Accounting

> "Every journal entry must balance - debits equal credits. The agent automatically determines:
>
> - Which account to **debit** (increase assets/expenses)
> - Which account to **credit** (increase liabilities/revenue)
> - The **transaction type** (receipt, expense, payroll, etc.)
> - A **confidence level** for the entry"

### 3. Running the Generator

> "Let me load the sample data..."
>
> [Load Simple or Complex scenario]
>
> "Each generated entry shows:
> - Date and description
> - Debit account and amount
> - Credit account and amount
> - Explanation of the accounting treatment"

### 4. Transaction Type Mapping

> "The rules engine maps transaction types to accounts:
>
> | Type | Debit | Credit |
> |------|-------|--------|
> | Receipt | Cash | Accounts Receivable |
> | Expense | Operating Expenses | Cash |
> | Payroll | Salaries & Wages | Cash |
> | Asset Purchase | Fixed Assets | Cash |
> | Depreciation | Depreciation Expense | Accumulated Depreciation |
>
> The LLM can handle more nuanced scenarios - like determining if a prepaid expense should hit Prepaid Assets vs Operating Expenses."

### 5. The Eval Suite

> "The eval tests entry generation against 12 labeled scenarios."
>
> [Click 'Run Eval Suite']
>
> "It measures:
> - **Debit accuracy** - correct debit account selection
> - **Credit accuracy** - correct credit account selection
> - **Type detection** - inferring transaction type from description
> - **Overall score** - combined accuracy"

---

## Chart of Accounts

> "The agent maps to a standard chart of accounts:
>
> **Assets**: Cash, Accounts Receivable, Inventory, Prepaid Expenses, Fixed Assets
>
> **Liabilities**: Accounts Payable, Accrued Expenses, Deferred Revenue, Notes Payable
>
> **Equity**: Retained Earnings
>
> **Revenue**: Service Revenue, Interest Income
>
> **Expenses**: Operating, Salaries, Depreciation, Utilities, etc.
>
> In production, this would connect to the client's actual chart of accounts."

---

## Complex Scenarios

> "The Complex scenario includes entries that challenge the system:
>
> - **Depreciation** - non-cash expense with contra-asset credit
> - **Deferred Revenue** - liability that converts to revenue over time
> - **Inventory/COGS** - multiple accounts involved in cost flow
> - **Loan Payments** - splitting principal vs interest
>
> These are where LLM reasoning really helps - understanding the business context."

---

## Why This Matters for Basis

> "Journal entries are the core of accounting. Get them wrong and:
> - Financial statements are incorrect
> - Tax filings have errors
> - Auditors flag issues
>
> The agent ensures consistent, correct entries while providing explanations for review."

---

## Technical Implementation

If asked about the technical side:

> "The rules engine uses a lookup table: transaction type → debit/credit accounts. The LLM gets:
> - A list of valid accounts with their types
> - Accounting principles (debits increase assets, etc.)
> - The transaction details
>
> It returns structured JSON with accounts, amounts, and explanations."

---

## Questions to Expect

**Q: How do you handle adjusting entries?**
> "Adjusting entries like accruals, deferrals, and depreciation are supported transaction types. The Complex scenario specifically tests these."

**Q: What about multi-line entries?**
> "Currently each entry is a simple debit/credit pair. In production, you'd need compound entries for things like payroll (multiple expense accounts, multiple liability accounts)."

**Q: How do you ensure GAAP compliance?**
> "The account mappings follow standard accounting treatment. The LLM is prompted with GAAP principles. But in production, entries would be reviewed before posting."

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
