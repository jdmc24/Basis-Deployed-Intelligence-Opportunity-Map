# Transaction Classifier Agent

An AI-powered agent that automatically categorizes bank transactions into accounting categories. Supports multiple processing engines including rule-based patterns and LLM-powered classification.

**[View Live Demo](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/agents/transaction-classifier/)**

---

## Overview

This agent analyzes bank statement transactions and assigns them to appropriate accounting categories like Revenue, Payroll, Travel, Software & Subscriptions, and more. It demonstrates how AI can automate one of the most time-consuming bookkeeping tasks.

## Features

- **Multi-Engine Processing** - Choose between Rules, Hybrid, Ollama, or OpenAI
- **Smart Classification** - Pattern matching + LLM reasoning
- **Confidence Scoring** - High/Medium/Low confidence indicators
- **Batch Processing** - Handle multiple transactions at once
- **Eval Suite** - Test accuracy against labeled ground truth data
- **Sample Data** - Pre-loaded transactions to demo immediately

## Processing Engines

| Engine | Icon | Description | Best For |
|--------|------|-------------|----------|
| **Rules** | ⚡ | Pattern-based keyword matching | Speed, no API costs |
| **Hybrid** | 🔀 | Rules first, LLM for ambiguous | Production balance |
| **Ollama** | 🦙 | Local LLM (Llama, Mistral, etc.) | Local testing |
| **OpenAI** | 🤖 | GPT-4o-mini via API | Highest accuracy |

### Why Multiple Engines?

- **Rules**: Fast and free - handles obvious transactions like "GUSTO PAYROLL" → Payroll
- **Hybrid**: Cost-effective - only calls LLM for transactions rules can't confidently classify
- **Ollama**: Test locally without API costs before deploying
- **OpenAI**: Maximum accuracy for ambiguous descriptions like "AMZN MKTP US"

## Classification Categories

| Category | Example Transactions |
|----------|---------------------|
| Revenue | Stripe transfers, client wires, check deposits |
| Payroll | Gusto payroll, ADP payments |
| Payroll Taxes | Gusto payroll taxes, tax deposits |
| Travel | Delta, United, Marriott, Uber |
| Software & Subscriptions | Adobe, Slack, Zoom, AWS |
| Office Supplies | Staples, Amazon office items |
| Utilities | Comcast, PG&E |
| Rent | Monthly rent payments |
| Insurance | State Farm, policy premiums |
| Bank Fees | Service charges, wire fees |

## Eval Suite

The built-in evaluation suite tests classification accuracy against 30 labeled test cases:

- **Ground Truth Data** - Manually labeled transactions with correct categories
- **Accuracy Metrics** - Percentage of correct classifications
- **Per-Category Breakdown** - See which categories perform best
- **Engine Comparison** - Compare Rules vs LLM accuracy

Run the eval suite to measure performance before and after changing models or prompts.

## Tech Stack

- **Vanilla JavaScript** - No framework dependencies
- **OpenAI API** - GPT-4o-mini for cloud LLM
- **Ollama** - Local LLM inference (localhost:11434)
- **CSS Variables** - Basis-inspired dark theme

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
