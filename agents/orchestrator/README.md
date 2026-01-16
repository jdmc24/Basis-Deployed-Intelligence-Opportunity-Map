# Multi-Agent Orchestrator

A 3-tier multi-agent orchestration system that mirrors Basis's production architecture for end-to-end bookkeeping automation.

## Architecture Overview

This implementation follows the same hierarchy described in the [OpenAI case study on Basis](https://openai.com/index/basis/):

```
                    ┌─────────────────────────┐
                    │   Coordination Agent    │  ← Layer 1: Routes tasks, spawns supervisors
                    └───────────┬─────────────┘
                                │
            ┌───────────────────┼───────────────────┐
            │                                       │
            ▼                                       ▼
┌───────────────────────┐             ┌───────────────────────┐
│ Data Entry Supervisor │             │ Verification Supervisor│  ← Layer 2: Manages sub-agents
└───────────┬───────────┘             └───────────┬───────────┘
            │                                      │
    ┌───────┴───────┐                              │
    │               │                              │
    ▼               ▼                              ▼
┌──────────┐  ┌──────────┐                  ┌──────────────────┐
│Classifier│  │ Journal  │                  │ Bank Reconciler  │  ← Layer 3: Specialized workers
└──────────┘  │ Entry    │                  └──────────────────┘
              └──────────┘
```

## The 3-Tier Pattern

| Layer | Role | Implementation |
|-------|------|---------------|
| **Coordination Agent** | Analyzes task complexity, spawns supervisors | Orchestrator core logic |
| **Supervising Agents** | Break down tasks, delegate to sub-agents | Data Entry + Verification Supervisors |
| **Sub-Agents** | Execute specialized tasks | Classifier, Journal Entry, Reconciliation |

### Layer 1: Coordination Agent
- Receives the incoming task (bank statement)
- Analyzes complexity and required operations
- Spawns appropriate supervising agents
- Aggregates final results

### Layer 2: Supervising Agents

**Data Entry Supervisor**
- Manages the data processing pipeline
- Coordinates Transaction Classifier → Journal Entry Generator
- Reports completion to Coordination Agent

**Verification Supervisor**
- Manages validation and reconciliation
- Delegates to Bank Reconciliation sub-agent
- Reports discrepancies to Coordination Agent

### Layer 3: Sub-Agents

**Transaction Classifier**
- Input: Raw bank transactions
- Output: Categorized transactions with confidence scores
- Reports to: Data Entry Supervisor

**Journal Entry Generator**
- Input: Classified transactions
- Output: Double-entry journal entries
- Reports to: Data Entry Supervisor

**Bank Reconciliation**
- Input: Bank statement + Journal entries
- Output: Reconciliation report with discrepancies
- Reports to: Verification Supervisor

## Features

### Real-Time Agent Activity Log
Watch the multi-agent communication in real-time:
- **Purple** entries: Coordination Agent decisions
- **Yellow** entries: Supervisor task delegation
- **Teal** entries: Sub-agent execution

### Visual Architecture Diagram
- Nodes light up as each agent becomes active
- Shows delegation flow from coordination → supervisor → sub-agent
- Nodes turn green upon completion

### Hierarchical Workflow Steps
- Indentation shows the agent hierarchy
- Coordination (no indent) → Supervisors (1 indent) → Sub-agents (2 indent)
- Each step shows status and results

## Workflow Execution

1. **Coordination Agent** receives bank statement
   - Analyzes: "35 transactions need: Classification → Journaling → Reconciliation"
   - Spawns: Data Entry Supervisor, Verification Supervisor

2. **Data Entry Supervisor** manages data processing
   - Delegates to Transaction Classifier
   - Receives results, delegates to Journal Entry Generator
   - Reports completion to Coordination Agent

3. **Verification Supervisor** manages validation
   - Delegates to Bank Reconciliation
   - Reports discrepancies to Coordination Agent

4. **Coordination Agent** aggregates results
   - Compiles unified results from all supervisors
   - Presents final dashboard

## Sample Data

35 transactions from a consulting firm's January bank statement:

| Category | Count | Examples |
|----------|-------|----------|
| Revenue | 8 | Stripe transfers, client wires |
| Payroll | 6 | Gusto payroll + taxes |
| Software | 8 | Adobe, Slack, AWS, etc. |
| Travel | 4 | Delta, Marriott, Uber |
| Operating | 9 | Rent, insurance, utilities |

**Built-in discrepancies for demo:**
- Duplicate transaction (INV1002)
- Some medium-confidence classifications

## Why This Architecture Matters

This 3-tier hierarchy enables:

1. **Scalability** - Add more supervisors/sub-agents without changing coordination logic
2. **Specialization** - Each sub-agent is optimized for its specific task
3. **Error Isolation** - Failures in one sub-agent don't crash the system
4. **Parallel Processing** - Supervisors can run sub-agents concurrently
5. **Human-in-the-loop** - Easy to add approval steps at supervisor level

## Technical Details

- Pure HTML/CSS/JavaScript (no build step)
- Runs entirely in browser
- Real data flows between agent layers
- Simulated async delays for realistic visualization

---

*Part of the [Basis Deployed Intelligence](../../) application for Jake McCorkle*
