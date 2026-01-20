# Multi-Agent Orchestrator

A 3-tier multi-agent orchestration system that mirrors Basis's production architecture for end-to-end bookkeeping automation. Supports multiple processing engines including rule-based patterns and LLM-powered classification.

**[View Live Demo](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/agents/orchestrator/)**

---

## Overview

This orchestrator coordinates multiple specialized AI agents to process a complete bookkeeping workflow: classify transactions, generate journal entries, and reconcile against bank statements. It demonstrates the same hierarchical architecture described in the [OpenAI case study on Basis](https://openai.com/index/basis/).

## Features

- **3-Tier Architecture** - Coordination → Supervision → Sub-Agents
- **Multi-Engine Processing** - Choose between Rules, Hybrid, Ollama, or OpenAI
- **Real-Time Activity Log** - Watch agents communicate and delegate
- **Visual Architecture Diagram** - See which agents are active
- **End-to-End Workflow** - Classification → Journal Entries → Reconciliation
- **Sample Data** - 35 transactions from a consulting firm

## Architecture

```
                    ┌─────────────────────────┐
                    │   Coordination Agent    │  ← Layer 1: Routes tasks
                    └───────────┬─────────────┘
                                │
            ┌───────────────────┼───────────────────┐
            │                                       │
            ▼                                       ▼
┌───────────────────────┐             ┌───────────────────────┐
│ Data Entry Supervisor │             │ Verification Supervisor│  ← Layer 2
└───────────┬───────────┘             └───────────┬───────────┘
            │                                      │
    ┌───────┴───────┐                              │
    ▼               ▼                              ▼
┌─────────┐   ┌─────────┐                   ┌─────────────┐
│Classifier│   │ Journal │                   │Reconciliation│  ← Layer 3
│  Agent   │   │  Agent  │                   │    Agent     │
└─────────┘   └─────────┘                   └─────────────┘
```

### Layer 1: Coordination Agent
- Receives the initial task (process bank statement)
- Analyzes complexity and determines required capabilities
- Spawns appropriate supervising agents
- Aggregates final results

### Layer 2: Supervising Agents
- **Data Entry Supervisor**: Manages classification and journal entry generation
- **Verification Supervisor**: Manages reconciliation and validation

### Layer 3: Sub-Agents
- **Transaction Classifier**: Categorizes transactions
- **Journal Entry Generator**: Creates double-entry records
- **Bank Reconciliation**: Matches and validates transactions

## Processing Engines

| Engine | Icon | Description | Best For |
|--------|------|-------------|----------|
| **Rules** | ⚡ | Pattern-based processing | Speed, consistency |
| **Hybrid** | 🔀 | Rules first, LLM for ambiguous | Production balance |
| **Ollama** | 🦙 | Local LLM (Llama, Mistral, etc.) | Local testing |
| **OpenAI** | 🤖 | GPT-4o-mini via API | Highest accuracy |

The selected engine is used by the Transaction Classifier sub-agent. Journal entries and reconciliation use rule-based logic.

## Workflow Steps

1. **Coordination Agent** analyzes the task and spawns supervisors
2. **Data Entry Supervisor** receives delegation
3. **Transaction Classifier** categorizes all transactions
4. **Journal Entry Generator** creates double-entry records
5. **Data Entry Supervisor** reports completion
6. **Verification Supervisor** receives delegation
7. **Bank Reconciliation** matches and validates
8. **Coordination Agent** aggregates results

## Output Summary

After processing, the orchestrator displays:
- Total transactions processed
- Revenue and expense totals
- Journal entries generated
- Reconciliation percentage
- Items requiring review

## Why This Architecture?

This mirrors how Basis structures their production system:
- **Scalability**: Each agent can be scaled independently
- **Specialization**: Agents are experts in their domain
- **Reliability**: Supervisors can retry failed sub-agent tasks
- **Observability**: Clear audit trail of agent decisions

## Tech Stack

- **Vanilla JavaScript** - No framework dependencies
- **OpenAI API** - GPT-4o-mini for cloud LLM
- **Ollama** - Local LLM inference (localhost:11434)
- **CSS Variables** - Basis-inspired dark theme

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
