# Bank Reconciliation - Interview Walkthrough

This document provides talking points for demonstrating the Bank Reconciliation agent during an interview.

---

## Opening Statement

> "Bank reconciliation is comparing what the bank says happened versus what's recorded in your books. You're looking for three things: transactions that match, transactions missing from one side, and amount discrepancies. This agent automates that matching process."

---

## Key Demo Points

### 1. The Engine Selector

> "Same pattern as the classifier - four processing modes:
>
> - **Rules** ⚡ - Multi-signal scoring algorithm. Fast and deterministic.
> - **Hybrid** 🔀 - Rules first, LLM reviews uncertain matches.
> - **Ollama** 🦙 - Local LLM for testing.
> - **OpenAI** 🤖 - LLM-powered fuzzy matching for complex cases."

### 2. The Matching Algorithm

> "The rules-based engine scores potential matches using multiple signals:
>
> | Signal | Weight | Description |
> |--------|--------|-------------|
> | **Amount** | 50 pts | Exact match - most reliable |
> | **Reference** | 30 pts | Check numbers, invoice IDs |
> | **Date** | 15 pts | Same day or within 3-5 days |
> | **Description** | 10 pts | Common words in vendor names |
>
> A score above 50 is considered a match. Below that, it's flagged for review."

### 3. Running a Reconciliation

> "Let me load the sample data..."
>
> [Upload bank CSV and books CSV, or click sample data]
>
> "The results show:
> - **Matched transactions** - paired correctly between bank and books
> - **Discrepancies** - items needing attention
> - **Summary stats** - total matched, reconciliation percentage"

### 4. LLM Matching Benefits

> "When I switch to OpenAI mode, the LLM can catch matches that rules miss. For example:
>
> - 'DELTA AIR' in the bank matching 'Delta - Client Travel' in the books
> - Different date formats or slight timing differences
> - Vendor name variations
>
> The LLM reasons about semantic similarity, not just exact patterns."

### 5. The Eval Suite

> "The eval tests matching accuracy against known correct pairs."
>
> [Click 'Run Eval Suite']
>
> "It measures:
> - **Match accuracy** - did we find the right pairs?
> - **Precision** - are we making false matches?
> - **Discrepancy detection** - did we catch the intentional mismatch?"

---

## Discrepancy Types

> "The agent identifies several types of discrepancies:
>
> | Type | Meaning | Action |
> |------|---------|--------|
> | **Missing from Books** | Bank has it, books don't | Record the transaction |
> | **Missing from Bank** | Books have it, bank doesn't | Check if it cleared |
> | **Duplicate** | Same entry appears twice | Remove duplicate |
> | **Amount Mismatch** | Matched but amounts differ | Investigate the variance |
>
> Each discrepancy has action buttons - 'Record', 'Remove', 'Investigate'."

---

## Why This Matters for Basis

> "Reconciliation is where errors surface. It's the verification step that catches:
> - Duplicate entries
> - Missed transactions
> - Data entry mistakes
> - Timing differences
>
> Basis clients need this to close their books monthly. The agent finds issues AND suggests fixes."

---

## Technical Implementation

If asked about the technical side:

> "The matching algorithm uses a weighted scoring system. Each potential match gets points for:
> - Exact amount match (50 points)
> - Reference number match (30 points)
> - Date proximity (up to 15 points)
> - Description similarity (up to 10 points)
>
> LLM matching sends each bank transaction to GPT-4o-mini with the full list of book entries, asking it to find the best match and explain why."

---

## Questions to Expect

**Q: How do you handle timing differences?**
> "The date scoring gives partial credit for transactions within 5 days. A transaction might show on the bank statement a few days after it was recorded in the books - that's normal."

**Q: What about partial matches?**
> "If amounts don't match exactly but everything else does, we flag it as an 'Amount Mismatch' discrepancy. The accountant can then investigate - maybe a fee was added, or there was a data entry error."

**Q: How accurate is the LLM matching?**
> "The eval suite measures this. Rules typically get 90%+ on clean data. LLM matching helps with the messy cases - inconsistent naming, abbreviations, slightly different amounts."

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
