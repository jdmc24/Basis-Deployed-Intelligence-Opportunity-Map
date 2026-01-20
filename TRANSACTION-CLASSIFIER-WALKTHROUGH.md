# Transaction Classifier - Interview Walkthrough

This document provides talking points for demonstrating the Transaction Classifier agent during an interview.

---

## Opening Statement

> "This agent takes raw bank statement transactions and categorizes them into accounting categories like Revenue, Payroll, Office Supplies, Travel, and more. This is typically one of the most time-consuming parts of bookkeeping - and it's exactly what Basis automates."

---

## Key Demo Points

### 1. The Engine Selector

> "I built four processing modes to demonstrate different approaches:
>
> - **Rules** ⚡ - Pattern matching. Fast, no API calls. If I see 'GUSTO PAYROLL' I know it's payroll.
> - **Hybrid** 🔀 - Rules first, then LLM for ambiguous transactions. This is the production-ready approach.
> - **Ollama** 🦙 - Local LLM for testing without API costs.
> - **OpenAI** 🤖 - Full LLM classification using GPT-4o-mini. Most accurate for edge cases."

**Why multiple engines?**
> "In production, you want flexibility. Rules handle 80% of transactions instantly and for free. The LLM handles the remaining 20% that need reasoning - like figuring out that 'AMZN MKTP US' is office supplies, not a stock purchase."

### 2. Running a Classification

> "Let me load the sample data and run a classification..."
>
> [Click 'Load Sample Data', then 'Classify Transactions']
>
> "You can see each transaction gets:
> - A **category** (Revenue, Payroll, etc.)
> - A **confidence level** (high/medium/low)
> - The **source** showing which engine classified it"

### 3. The Eval Suite

> "I added an evaluation suite with 30 labeled test cases. This is critical for any ML system - you need to measure accuracy before and after making changes."
>
> [Click 'Run Eval Suite']
>
> "The eval shows:
> - **Overall accuracy** - percentage of correct classifications
> - **Per-transaction results** - see exactly which ones failed
>
> This lets you compare Rules vs LLM accuracy, or test how a prompt change affects performance."

### 4. Hybrid Mode Deep Dive

> "Let me show you how Hybrid mode works..."
>
> [Switch to Hybrid, run classification]
>
> "Watch the source column - you'll see some say 'Rules' and others say 'OpenAI (LLM assist)'. The system:
> 1. Tries rules first
> 2. If confidence is low, sends to the LLM
> 3. Only pays for API calls when needed
>
> This is how you balance cost and accuracy in production."

---

## Classification Logic

If asked about how classification works:

### Rules Engine
> "The rules engine uses pattern matching:
> - 'GUSTO PAYROLL' + negative amount → Payroll
> - 'STRIPE TRANSFER' + positive amount → Revenue
> - 'THOMSON REUTERS' → Software & Subscriptions
>
> Simple, fast, deterministic."

### LLM Engine
> "The LLM gets context about valid categories and accounting rules. It can reason about:
> - What 'AMZN MKTP US' likely means (office supplies, not stock)
> - Whether 'DELTA AIR' is Travel or a dividend (it's Travel)
> - Ambiguous vendor names that rules can't handle"

---

## Why This Matters for Basis

> "Transaction classification is step one in the bookkeeping workflow. Get this wrong, and everything downstream - journal entries, reports, reconciliation - is wrong too.
>
> The multi-engine approach shows I understand:
> - **Cost optimization** - don't call LLMs when rules work fine
> - **Accuracy requirements** - use LLMs for the hard cases
> - **Evaluation discipline** - measure everything before deploying"

---

## Technical Implementation

If asked about the technical side:

> "It's built with vanilla JavaScript - no React or Vue. The LLM integration uses:
> - **OpenAI API** with GPT-4o-mini (cheap and fast)
> - **Ollama** for local testing with Llama 3.2 or Mistral
> - **Prompt engineering** to get consistent JSON responses"

---

## Questions to Expect

**Q: Why not use LLMs for everything?**
> "Cost and latency. If I can classify 'GUSTO PAYROLL' with a simple regex, why spend 0.1 cents and 200ms on an API call? Rules handle the obvious stuff; LLMs handle the hard stuff."

**Q: How would you improve accuracy?**
> "More training data, better prompts, and feedback loops. In production, I'd track when users override classifications and use that to improve the rules and fine-tune prompts."

**Q: What about edge cases?**
> "That's what the Hybrid mode is for. If rules can't confidently classify something, it automatically escalates to the LLM. And the eval suite helps catch systematic failures."

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
