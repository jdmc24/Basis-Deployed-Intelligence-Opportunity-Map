# Bank Reconciliation Agent

An AI-powered agent that automatically matches bank statement transactions to book entries and identifies discrepancies. Supports multiple processing engines including rule-based matching and LLM-powered analysis.

**[View Live Demo](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/agents/bank-reconciliation/)**

---

## Overview

This agent compares bank statement data against accounting book entries, automatically matching transactions and flagging discrepancies that need human review. It demonstrates how AI can automate the tedious reconciliation process.

## Features

- **Multi-Engine Processing** - Choose between Rules, Hybrid, Ollama, or OpenAI
- **Smart Matching** - Multi-signal scoring algorithm
- **Discrepancy Detection** - Automatically flags mismatches and duplicates
- **Action Buttons** - Resolve discrepancies with one click
- **Eval Suite** - Test matching accuracy against labeled data
- **Dual Upload** - Load bank statement and book entries separately

## Processing Engines

| Engine | Icon | Description | Best For |
|--------|------|-------------|----------|
| **Rules** | ⚡ | Multi-signal scoring algorithm | Speed, deterministic |
| **Hybrid** | 🔀 | Rules first, LLM for uncertain | Production balance |
| **Ollama** | 🦙 | Local LLM (Llama, Mistral, etc.) | Local testing |
| **OpenAI** | 🤖 | GPT-4o-mini via API | Fuzzy matching |

## Matching Algorithm

The rules-based engine scores potential matches using multiple signals:

| Signal | Weight | Description |
|--------|--------|-------------|
| **Amount** | 50 pts | Exact amount match (most reliable) |
| **Reference** | 30 pts | Matching reference/check numbers |
| **Date** | 15 pts | Same day or within 3-5 days |
| **Description** | 10 pts | Common words in vendor names |

Transactions scoring ≥50 points are considered matched.

### LLM Matching

When using OpenAI or Ollama engines, the LLM analyzes:
- Semantic similarity between descriptions
- Date proximity reasoning
- Amount matching with tolerance
- Reference number correlation

This catches matches that rule-based scoring might miss, like "DELTA AIR" matching "Delta - Client Travel".

## Discrepancy Types

| Type | Description | Suggested Action |
|------|-------------|------------------|
| **Missing from Books** | Bank transaction with no book match | Record the transaction |
| **Missing from Bank** | Book entry with no bank match | Verify timing, investigate |
| **Duplicate** | Same transaction appears multiple times | Remove duplicate |
| **Amount Mismatch** | Matched but amounts differ | Investigate variance |

## Eval Suite

The built-in evaluation suite tests matching accuracy:

- **15 Test Transactions** - Bank and book entries with known correct matches
- **Match Accuracy** - Percentage of correctly paired transactions
- **Precision Score** - False positive rate measurement
- **Discrepancy Detection** - Verifies intentional mismatches are caught

## Tech Stack

- **Vanilla JavaScript** - No framework dependencies
- **OpenAI API** - GPT-4o-mini for cloud LLM
- **Ollama** - Local LLM inference (localhost:11434)
- **CSS Variables** - Basis-inspired dark theme

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
