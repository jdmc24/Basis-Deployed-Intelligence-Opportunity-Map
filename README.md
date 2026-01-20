# Basis Deployed Intelligence Application

A demonstration project showcasing AI-powered accounting automation, built as part of a job application for [Basis](https://www.getbasis.ai/).

**[View Live Demo](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/intelligence-map/)**

---

## Project Overview

This project demonstrates two key capabilities:

1. **Market Intelligence** - Identifying ideal CPA firm customers for Basis
2. **AI Agent Development** - Building accounting automation tools that mirror Basis's architecture

---

## Intelligence Map

An interactive dashboard visualizing 45 target CPA firms across the United States, scored and prioritized based on their fit for Basis's platform.

**Features:**
- Interactive US map with firm locations
- Priority scoring (High/Medium/Low) based on CAS focus, tech adoption, and growth signals
- Filtering by priority, state, and firm name
- Detailed firm profiles on click

**[View Intelligence Map →](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/intelligence-map/)**

---

## AI Agents

Four specialized agents demonstrating core bookkeeping automation capabilities:

### Transaction Classifier
Automatically categorizes bank transactions into accounting categories (Revenue, Payroll, Travel, etc.).

### Bank Reconciliation
Matches bank statement transactions to book entries and identifies discrepancies.

### Journal Entry Generator
Creates double-entry journal entries with appropriate debit/credit accounts.

### Multi-Agent Orchestrator
Coordinates all agents in a 3-tier architecture mirroring Basis's production system (Coordination → Supervision → Sub-Agents).

---

## Key Technical Features

**Multi-Engine Processing**
Each agent supports four processing modes:
- **Rules** - Fast pattern matching, no API costs
- **Hybrid** - Rules first, LLM for ambiguous cases
- **Ollama** - Local LLM testing (Llama, Mistral)
- **OpenAI** - Cloud LLM via GPT-4o-mini

**Evaluation Suite**
Built-in eval suites with labeled test data to measure accuracy across different engines and configurations.

---

## Tech Stack

- Vanilla JavaScript (no frameworks)
- Leaflet.js for mapping
- OpenAI API / Ollama for LLM integration
- GitHub Pages for hosting

---

## Repository Structure

```
├── intelligence-map/      # Target firm dashboard
│   ├── index.html
│   └── README.md
├── agents/
│   ├── transaction-classifier/
│   ├── bank-reconciliation/
│   ├── journal-entry-generator/
│   └── orchestrator/
└── README.md              # This file
```

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
