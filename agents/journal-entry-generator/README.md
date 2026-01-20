# Journal Entry Generator

An AI-powered agent that automatically generates double-entry journal entries from source transactions. Supports multiple processing engines including rule-based patterns and LLM-powered account selection.

**[View Live Demo](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/agents/journal-entry-generator/)**

---

## Overview

This agent analyzes transactions and generates proper double-entry journal entries with appropriate debit and credit accounts. It demonstrates how AI can automate the creation of accounting records while maintaining GAAP compliance.

## Features

- **Multi-Engine Processing** - Choose between Rules, Hybrid, Ollama, or OpenAI
- **Double-Entry Generation** - Automatic debit/credit account selection
- **Transaction Type Detection** - Infers type from description and amount
- **AI Explanations** - LLM-generated reasoning for each entry
- **Eval Suite** - Test entry accuracy against labeled data
- **Sample Scenarios** - Simple and complex transaction sets

## Processing Engines

| Engine | Icon | Description | Best For |
|--------|------|-------------|----------|
| **Rules** | ⚡ | Pattern-based account mapping | Speed, consistency |
| **Hybrid** | 🔀 | Rules first, LLM for complex | Production balance |
| **Ollama** | 🦙 | Local LLM (Llama, Mistral, etc.) | Local testing |
| **OpenAI** | 🤖 | GPT-4o-mini via API | Complex scenarios |

## Supported Transaction Types

| Type | Debit Account | Credit Account |
|------|---------------|----------------|
| **Receipt** | Cash | Accounts Receivable |
| **Expense** | Operating Expenses | Cash |
| **Payroll** | Salaries & Wages | Cash |
| **Payroll Taxes** | Payroll Tax Expense | Cash |
| **Asset Purchase** | Fixed Assets | Cash |
| **Prepaid Expense** | Prepaid Expenses | Cash |
| **Depreciation** | Depreciation Expense | Accumulated Depreciation |
| **Inventory** | Inventory | Cash |
| **COGS** | Cost of Goods Sold | Inventory |
| **Loan Payment** | Notes Payable | Cash |
| **Deferred Revenue** | Cash | Deferred Revenue |
| **Revenue Recognition** | Deferred Revenue | Service Revenue |
| **Dividend** | Retained Earnings | Dividends Payable |

## Chart of Accounts

The agent maps to a standard chart of accounts:

**Assets**: Cash, Accounts Receivable, Inventory, Prepaid Expenses, Fixed Assets
**Contra-Assets**: Accumulated Depreciation, Allowance for Doubtful Accounts
**Liabilities**: Accounts Payable, Accrued Expenses, Deferred Revenue, Notes Payable
**Equity**: Retained Earnings, Dividends Payable
**Revenue**: Service Revenue, Interest Income
**Expenses**: Operating, Salaries, Depreciation, Interest, Utilities, etc.

## Eval Suite

The built-in evaluation suite tests entry generation accuracy:

- **12 Test Cases** - Transactions with known correct entries
- **Debit Accuracy** - Correct debit account selection rate
- **Credit Accuracy** - Correct credit account selection rate
- **Type Detection** - Transaction type inference accuracy
- **Overall Score** - Combined accuracy metric

## Tech Stack

- **Vanilla JavaScript** - No framework dependencies
- **OpenAI API** - GPT-4o-mini for cloud LLM
- **Ollama** - Local LLM inference (localhost:11434)
- **CSS Variables** - Basis-inspired dark theme

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
