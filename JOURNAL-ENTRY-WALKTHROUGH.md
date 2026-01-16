# Journal Entry Generator - Interview Walkthrough

Use this document to guide your discussion of the Journal Entry Generator during your Basis interview.

---

## The Problem

**What accountants deal with today:**
- Every transaction needs a proper journal entry with debits and credits
- Accountants must know the correct accounts to use for each transaction type
- Different transaction types require different entry patterns (prepaid vs expense, asset purchase vs expense, etc.)
- Month-end adjusting entries (accruals, deferrals, depreciation) are easy to forget or miscalculate
- New staff need significant training to understand proper entry construction

**Why this matters to Basis:**
- Journal entry creation is mentioned in Basis's core use cases
- Basis specifically highlights "AI-generated explanations" as a differentiator
- This agent demonstrates understanding of double-entry bookkeeping fundamentals
- The confidence scoring shows how AI can flag items needing human review

---

## The Solution

**A Journal Entry Generator Agent that:**
1. Accepts CSV upload of source transactions (or sample data)
2. Analyzes each transaction to determine entry type
3. Generates proper double-entry journal entries with:
   - Correct debit and credit accounts
   - Account type classifications (Asset, Liability, Equity, Revenue, Expense)
   - AI-generated explanations of the accounting logic
   - Confidence scoring for review prioritization
4. Handles 19 different transaction types including complex adjustments

---

## Design Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Input method | Single CSV + preview option | Simple, with ability to review data before processing |
| Entry format | Standard two-line format | Matches how journal entries appear in GL software |
| Confidence levels | High (95%+), Medium (80-94%) | Helps accountants prioritize review |
| Explanations | Plain English | Matches Basis's emphasis on explainable AI |
| Transaction types | 19 types | Covers standard + advanced entries |

---

## Technical Implementation

### Transaction Type Inference

The agent analyzes descriptions and amounts to infer entry type:

```javascript
function inferType(transaction) {
    const desc = transaction.description.toLowerCase();
    const amount = transaction.amount;

    // Keyword matching for specific types
    if (desc.includes('payroll')) return 'payroll';
    if (desc.includes('depreciation')) return 'depreciation';
    if (desc.includes('prepaid')) return 'prepaid';
    if (desc.includes('inventory')) return 'inventory';
    if (desc.includes('equipment')) return 'asset';
    if (desc.includes('deferred revenue')) return 'deferred';
    if (desc.includes('accrued')) return 'accrual';

    // Fall back to amount-based inference
    if (amount > 0) return 'receipt';
    return 'expense';
}
```

**Why this approach:**
- Keywords capture explicit transaction types
- Amount sign (positive/negative) handles general cases
- Falls back gracefully when description is ambiguous

### Entry Generation Rules

Each transaction type maps to a specific entry pattern:

| Type | Debit | Credit | Confidence |
|------|-------|--------|------------|
| receipt | Cash | Accounts Receivable/Revenue | High |
| expense | Operating Expenses | Cash/Accounts Payable | High |
| payroll | Salaries & Wages Expense | Cash | High |
| prepaid | Prepaid Expenses | Cash | High |
| asset | Fixed Assets | Cash/Accounts Payable | High |
| depreciation | Depreciation Expense | Accumulated Depreciation | High |
| deferred | Cash | Deferred Revenue | High |
| recognition | Deferred Revenue | Service Revenue | High |
| accrual | Expense Account | Accrued Liabilities | Medium |

**Medium confidence** is assigned when:
- Transaction type requires judgment (accruals, estimates)
- Description is ambiguous
- Could reasonably be categorized multiple ways

---

## Sample Data Strategy

**Created two scenarios:**

### Simple Scenario (15 transactions)
- Basic cash receipts from customers
- Standard operating expenses
- Payroll entries
- Interest income
- All straightforward, high-confidence entries

**Purpose:** Shows core functionality with typical small business transactions

### Complex Scenario (25 transactions)
- Prepaid expenses (insurance)
- Fixed asset purchases (equipment)
- Deferred revenue (annual contracts)
- Depreciation entries
- Accrued expenses and revenue
- COGS entries
- Loan principal and interest
- Dividend declarations
- Month-end adjusting entries

**Purpose:** Shows handling of sophisticated accounting scenarios

---

## Key Features to Highlight

### 1. Preview Data Button
- User can see sample data before loading it
- Modal shows all transactions in table format
- Color-coded amounts (green positive, red negative)
- Builds trust - user knows what they're working with

### 2. Double-Entry Validation
- Every entry has equal debits and credits
- Summary shows total debits = total credits
- Demonstrates fundamental accounting principle

### 3. Confidence Scoring
- High (95%+): Standard, clear-cut entries
- Medium (80-94%): May need review
- Summary cards show count of each
- Helps accountants prioritize review time

### 4. AI Explanations
- Each entry includes plain-English explanation
- Explains the "why" not just the "what"
- Matches Basis's differentiator of explainable AI

---

## What This Demonstrates About Me

**Technical skills:**
- Can implement rule-based classification systems
- Understand how to combine heuristics with confidence scoring
- UI/UX thinking (preview modal, expandable cards)

**Domain knowledge:**
- Deep understanding of double-entry bookkeeping
- Know various entry types beyond basics (accruals, deferrals, COGS)
- Understand month-end adjusting entries

**Product thinking:**
- Preview feature builds user trust
- Confidence scoring enables efficient review workflows
- Explanations make AI decisions transparent

---

## How This Relates to Basis

From the OpenAI article on Basis:
> "Journal entries with AI-generated explanations of logic, data sources, and confidence levels"

**This agent directly demonstrates:**
- Journal entry generation ✓
- AI-generated explanations ✓
- Confidence levels ✓

**Missing (would add):**
- Data sources (showing where the transaction came from)
- Integration with actual GL systems

---

## Demo Script (3-4 minutes)

1. **Open the Journal Entry Generator page**
   - Point out the clean interface

2. **Click "Preview Data" under Simple Scenario**
   - Show the modal with 15 transactions
   - "Users can review the data before processing"
   - Close modal

3. **Click "Simple Scenario" then "Generate Journal Entries"**
   - Walk through summary cards: "15 entries, $35K in debits, all balanced"
   - "15 high confidence - these are straightforward"

4. **Click on an entry to expand**
   - Show the debit/credit accounts
   - Read the AI explanation
   - "This explains the accounting logic in plain English"

5. **Try the Complex Scenario**
   - "Now let's try more sophisticated transactions"
   - Click Preview first: "Accruals, depreciation, deferrals..."
   - Load and Generate
   - Show some medium-confidence entries: "These might need review"

6. **Expand a complex entry (depreciation or deferred revenue)**
   - Show how the explanation helps understand the entry
   - "An accountant can quickly verify this is correct"

**Time: ~4 minutes**

---

## Comparison to Other Agents

| Aspect | Transaction Classifier | Bank Reconciliation | Journal Entry Generator |
|--------|------------------------|---------------------|-------------------------|
| Input | Transaction list | Two files (comparison) | Transaction list |
| Core logic | Categorization | Matching | Generation |
| Output | Categories + confidence | Discrepancy report | Journal entries |
| AI role | Classifies ambiguous | Suggests fixes | Explains entries |
| Accounting concept | Chart of accounts | Reconciliation | Double-entry |

**Together the three agents show:**
- Different types of accounting automation
- Classification, matching, AND generation
- Comprehensive understanding of CAS workflows
- Both rule-based and AI-enhanced approaches

---

## Questions to Ask / Discuss

**To show deeper thinking:**

1. "How does Basis handle multi-leg journal entries? Sometimes one transaction needs more than two lines."

2. "Do you find accountants trust AI-generated entries more when explanations are provided?"

3. "How do you handle reversing entries or corrections to previously-generated entries?"

4. "What's the most complex entry type your agents handle - intercompany transactions? Payroll with multiple deductions?"

---

## Potential Follow-up Discussion

If the interviewer asks "what would you add?":

1. **Multi-leg entries** - Some transactions need 3+ lines (payroll with deductions)
2. **Batch approval** - Approve multiple entries at once
3. **Export to GL** - Push entries directly to QuickBooks/Xero
4. **Entry templates** - Save common entry patterns for reuse
5. **Audit trail** - Track who approved each entry and when

---

## Files Reference

```
basis-target-map/
├── agents/
│   └── journal-entry-generator/
│       ├── index.html          # Main interface + all logic
│       └── README.md           # Public documentation
└── JOURNAL-ENTRY-WALKTHROUGH.md  # This file (private)
```

---

*Keep this document private - it's your interview prep, not public documentation.*
