# Multi-Agent Orchestrator - Interview Walkthrough

This document provides talking points for demonstrating the Multi-Agent Orchestrator during an interview.

---

## Opening Statement

> "This orchestrator coordinates multiple specialized AI agents to process a complete bookkeeping workflow. It mirrors the exact 3-tier architecture described in the OpenAI case study on Basis - Coordination Agent at the top, Supervising Agents in the middle, and Sub-Agents doing the actual work."

---

## Key Demo Points

### 1. The 3-Tier Architecture

> "Let me walk you through the layers:
>
> **Layer 1 - Coordination Agent**
> - Receives the initial task
> - Analyzes complexity
> - Spawns appropriate supervisors
>
> **Layer 2 - Supervising Agents**
> - Data Entry Supervisor manages classification and journal entries
> - Verification Supervisor manages reconciliation
>
> **Layer 3 - Sub-Agents**
> - Transaction Classifier
> - Journal Entry Generator
> - Bank Reconciliation
>
> Watch the architecture diagram light up as agents activate."

### 2. The Engine Selector

> "Same four engines as the individual agents:
>
> - **Rules** ⚡ - Fast pattern-based processing
> - **Hybrid** 🔀 - Rules + LLM for ambiguous cases
> - **Ollama** 🦙 - Local LLM testing
> - **OpenAI** 🤖 - Full LLM classification
>
> The selected engine is used by the Transaction Classifier sub-agent."

### 3. Running the Workflow

> "Let me load the sample data - 35 transactions from a consulting firm..."
>
> [Click 'Load Sample Data', then 'Run Full Workflow']
>
> "Watch the activity log - you can see agents communicating:
> - Coordination Agent spawning supervisors
> - Supervisors delegating to sub-agents
> - Sub-agents reporting results back up the chain
>
> The architecture diagram shows which agent is currently active."

### 4. The Activity Log

> "The log shows the agent communication in real-time:
>
> - **[Coordination]** messages in teal
> - **[Supervisor]** messages showing delegation
> - **[Sub-Agent]** messages showing actual work
>
> This mirrors what you'd see in production logging - essential for debugging and auditing."

### 5. Results Tabs

> "After processing, you get three result tabs:
>
> - **Classified Transactions** - categories and confidence levels
> - **Journal Entries** - double-entry records with explanations
> - **Reconciliation** - matched transactions and discrepancies
>
> Plus a summary panel with totals and key metrics."

---

## Why This Architecture?

> "This mirrors how Basis structures their production system:
>
> **Scalability** - Each agent can be scaled independently. High transaction volume? Scale up the classifier.
>
> **Specialization** - Agents are experts in their domain. The classifier only knows classification.
>
> **Reliability** - Supervisors can retry failed sub-agent tasks. If reconciliation fails, retry without re-running classification.
>
> **Observability** - Clear audit trail. You can see exactly which agent made which decision."

---

## The OpenAI Case Study Reference

> "The [OpenAI case study on Basis](https://openai.com/index/basis/) describes this exact pattern:
>
> - Coordination agents that route and spawn
> - Supervising agents that manage workflows
> - Specialized sub-agents that do the work
>
> I built this to demonstrate understanding of how Basis actually works in production."

---

## Technical Implementation

If asked about the technical side:

> "The workflow is async JavaScript with simulated delays to show the agent communication clearly. In production:
>
> - Each agent would be a separate service
> - Communication via message queues
> - State persisted in a database
> - Real async processing
>
> The demo compresses what might take minutes into seconds for demo purposes."

---

## Questions to Expect

**Q: Why not just one agent that does everything?**
> "Separation of concerns. Each agent can be updated, scaled, and monitored independently. The classifier team doesn't need to understand reconciliation logic."

**Q: How do agents communicate?**
> "In this demo, it's function calls. In production, you'd use message queues (like SQS or RabbitMQ) so agents can be distributed across servers."

**Q: What happens when an agent fails?**
> "The supervisor catches the error and can retry, use a fallback, or escalate to human review. The coordination agent gets notified either way."

**Q: How do you handle high volume?**
> "Horizontal scaling - run multiple instances of each agent type. The supervisors distribute work across available workers."

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
