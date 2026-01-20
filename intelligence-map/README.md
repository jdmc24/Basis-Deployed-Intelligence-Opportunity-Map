# Basis Target Intelligence Map

An interactive dashboard identifying CPA firms that would be ideal customers for [Basis](https://www.getbasis.ai/), an AI platform for accounting firms.

**[View Live Demo](https://jdmc24.github.io/Basis-Deployed-Intelligence-Application/intelligence-map/)**

---

## Overview

This dashboard visualizes 45 target CPA firms across the United States, scored and prioritized based on their fit for Basis's AI-powered accounting automation platform.

## Features

- **Interactive US Map** - Leaflet-powered visualization with firm locations
- **Priority Scoring** - High/Medium/Low ratings based on fit criteria
- **Filtering & Search** - Filter by priority, state, or search by firm name
- **Firm Details** - Click any firm to see detailed profile information
- **Agent Navigation** - Quick links to all 4 AI agent demos

## Scoring Criteria

Firms are scored based on factors that indicate good fit for Basis:

| Factor | Weight | Description |
|--------|--------|-------------|
| CAS Focus | High | Firms emphasizing Client Accounting Services |
| Tech Forward | High | Evidence of technology adoption |
| Growth Mode | Medium | Actively expanding or hiring |
| Firm Size | Medium | Mid-market firms (50-500 employees) |
| Geographic | Low | Presence in tech-friendly markets |

## Priority Breakdown

| Priority | Count | Criteria |
|----------|-------|----------|
| **High** | 15 firms | Strong CAS focus + tech adoption signals |
| **Medium** | 20 firms | Good fit with some gaps |
| **Low** | 10 firms | Potential fit, needs validation |

## Data Sources

- Firm websites and LinkedIn profiles
- Accounting Today Top 100
- CPA Practice Advisor rankings
- Regional business journals

## Tech Stack

- **Leaflet.js** - Interactive mapping
- **Vanilla JavaScript** - No framework dependencies
- **CSS Grid/Flexbox** - Responsive layout
- **GitHub Pages** - Static hosting

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
