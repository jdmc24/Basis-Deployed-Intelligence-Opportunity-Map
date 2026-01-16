# Multi-Agent Orchestrator - Interview Walkthrough

Use this document to guide your discussion of the Multi-Agent Orchestrator during your Basis interview.

---

## The Architecture (Mirrors Basis Production)

This implementation follows the exact 3-tier hierarchy described in the [OpenAI case study on Basis](https://openai.com/index/basis/):

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

---

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

---

## Why This Architecture Matters

This 3-tier hierarchy enables:

1. **Scalability** - Add more supervisors/sub-agents without changing coordination logic
2. **Specialization** - Each sub-agent is optimized for its specific task
3. **Error Isolation** - Failures in one sub-agent don't crash the system
4. **Parallel Processing** - Supervisors can run sub-agents concurrently
5. **Human-in-the-loop** - Easy to add approval steps at supervisor level

---

## Key Features to Highlight

### 1. Preview Data Button
- Users can see sample data before loading
- Builds trust - no surprises about what's being processed
- Shows transaction summary (deposits, withdrawals, count)

### 2. Real-Time Agent Activity Log
Watch the multi-agent communication in real-time:
- **Purple** entries: Coordination Agent decisions
- **Yellow** entries: Supervisor task delegation
- **Teal** entries: Sub-agent execution

### 3. Visual Architecture Diagram
- Nodes light up as each agent becomes active
- Shows delegation flow from coordination → supervisor → sub-agent
- Nodes turn green upon completion

### 4. Hierarchical Workflow Steps
- Indentation shows the agent hierarchy
- Coordination (no indent) → Supervisors (1 indent) → Sub-agents (2 indent)
- Each step shows status and results

### 5. Actionable Discrepancy Resolution
Users can take action on flagged items:
- **Duplicates**: Delete Duplicate or Keep Both
- **Low Confidence**: Reclassify with category picker
- **All items**: Mark as Reviewed

The summary cards update in real-time as items are resolved.

---

## Demo Script (4-5 minutes)

1. **Open the Multi-Agent Orchestrator page**
   - Point out the 3-tier architecture badge
   - Show the architecture diagram: "This mirrors Basis's production architecture"

2. **Click Preview to show sample data**
   - "Users can review the data before processing"
   - Show the summary: "35 transactions, $59K in deposits, $53K in withdrawals"
   - Close modal

3. **Click Load Sample Data, then Run Multi-Agent Workflow**
   - Watch the agent log: "See how the Coordination Agent spawns supervisors..."
   - Point out the color coding: purple for coordination, yellow for supervisors, teal for sub-agents
   - Watch the architecture diagram light up

4. **Review the results**
   - Walk through summary cards: "35 transactions processed, 91% reconciled"
   - "3 items flagged for review"

5. **Show the Reconciliation tab**
   - Point out the action buttons
   - Click "Delete Duplicate" on one: "Watch the metrics update in real-time"
   - Click "Reclassify" on another: Show the category picker

6. **Explain the architecture choice**
   - "This 3-tier pattern allows Basis to scale - you can add more supervisors for new capabilities without changing the coordination logic"
   - "Error isolation means a bug in one sub-agent doesn't crash the whole system"

**Time: ~5 minutes**

---

## What This Demonstrates About Me

**Technical skills:**
- Can implement multi-agent orchestration patterns
- Understand agent hierarchy and delegation
- UI/UX thinking (real-time feedback, action buttons)

**Architecture understanding:**
- Deep understanding of the Basis multi-agent pattern
- Know why this architecture was chosen over alternatives
- Can articulate trade-offs (complexity vs. scalability)

**Product thinking:**
- Preview feature builds user trust
- Action buttons make workflow interactive
- Real-time updates show system responsiveness

---

## How This Relates to Basis

From the OpenAI article on Basis:
> "When a task is assigned to a coordination agent, it assesses the complexity and either handles it directly or delegates tasks to one or more supervisors."

**This orchestrator directly demonstrates:**
- Coordination Agent ✓
- Supervising Agents ✓
- Sub-Agents ✓
- Task delegation based on complexity ✓

**What I'd add in production:**
- More supervising agents for different domains (Tax, Audit, Advisory)
- Dynamic supervisor spawning based on task analysis
- Parallel sub-agent execution within supervisors
- Human approval gates at supervisor level

---

## Questions to Ask / Discuss

**To show deeper thinking:**

1. "How does Basis decide when to spawn additional supervisors versus having one supervisor handle everything?"

2. "Do supervisors ever communicate laterally, or is all coordination routed through the top-level agent?"

3. "How do you handle failures in sub-agents - does the supervisor retry, escalate, or request human intervention?"

4. "What's the typical latency for end-to-end workflows? Do you parallelize sub-agents within a supervisor?"

---

## Potential Follow-up Discussion

If the interviewer asks "what would you add?":

1. **More supervisors** - Tax Supervisor, Audit Supervisor, Advisory Supervisor
2. **Parallel execution** - Run independent sub-agents concurrently
3. **Human-in-the-loop gates** - Approval checkpoints at supervisor level
4. **Agent performance metrics** - Track accuracy and latency per agent
5. **Dynamic routing** - Let coordination agent learn optimal delegation patterns

---

## Comparison to Other Agents

| Aspect | Individual Agents | Orchestrator |
|--------|------------------|--------------|
| Scope | Single task | End-to-end workflow |
| Architecture | Flat | 3-tier hierarchy |
| Output | Single result | Unified dashboard |
| User interaction | Per-agent | Centralized |
| Demonstrates | Individual skills | System design |

**The orchestrator shows I understand:**
- Not just individual agent capabilities
- But how to coordinate them at scale
- Following Basis's exact production pattern

---

## Files Reference

```
basis-target-map/
├── agents/
│   └── orchestrator/
│       ├── index.html          # Main interface + all logic
│       └── README.md           # Public documentation
└── ORCHESTRATOR-WALKTHROUGH.md  # This file (private)
```

---

*Keep this document private - it's your interview prep, not public documentation.*
