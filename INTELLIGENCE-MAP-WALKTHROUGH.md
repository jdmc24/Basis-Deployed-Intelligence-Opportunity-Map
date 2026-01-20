# Intelligence Map - Interview Walkthrough

This document provides talking points for demonstrating the Basis Target Intelligence Map during an interview.

---

## Opening Statement

> "This is an interactive dashboard I built to identify CPA firms that would be ideal customers for Basis. It visualizes 45 target firms across the US, scored and prioritized based on their fit for Basis's AI-powered accounting automation."

---

## Key Demo Points

### 1. The Map Interface

> "The map shows firm locations with color-coded markers:
> - **Green** = High priority targets
> - **Yellow** = Medium priority
> - **Gray** = Lower priority, but still potential fits
>
> Click any marker to see the firm's profile - their location, size, and why they're a good fit for Basis."

### 2. Scoring Methodology

> "I developed a scoring system based on factors that indicate good Basis fit:
>
> - **CAS Focus** - Are they emphasizing Client Accounting Services?
> - **Tech Forward** - Evidence of technology adoption?
> - **Growth Mode** - Actively expanding or hiring?
> - **Firm Size** - Mid-market firms tend to be ideal
>
> High-priority firms scored well across multiple factors."

### 3. Filtering & Search

> "The sidebar lets you filter firms by:
> - Priority level (High/Medium/Low)
> - State
> - Or search by firm name
>
> This is useful for territory planning or targeting specific regions."

### 4. Agent Navigation

> "Notice the navigation at the top - this dashboard connects to four AI agent demos:
> - Transaction Classifier
> - Bank Reconciliation
> - Journal Entry Generator
> - Multi-Agent Orchestrator
>
> Each demonstrates a core Basis capability."

---

## Research Highlights

> "The research behind this involved:
> - Analyzing Accounting Today Top 100 lists
> - Reviewing firm websites for CAS offerings
> - Checking LinkedIn for growth signals
> - Cross-referencing CPA Practice Advisor rankings
>
> The goal was to identify firms where Basis could deliver the most value - firms doing high-volume CAS work who would benefit from AI automation."

---

## Why This Matters for Basis

> "This demonstrates several things:
>
> 1. **Market Research Skills** - Understanding the CPA landscape
> 2. **Strategic Thinking** - Identifying ideal customer profiles
> 3. **Technical Execution** - Building a functional tool, not just a report
> 4. **Data Visualization** - Making complex data accessible
>
> These are the same skills I'd apply to understanding Basis's market and customers."

---

## Technical Implementation

If asked about the technical side:

> "The map is built with:
> - **Leaflet.js** for the interactive mapping
> - **Vanilla JavaScript** - no heavy frameworks
> - **GitHub Pages** for hosting
>
> The firm data is embedded in the page for simplicity, but in production this would connect to a CRM or database."

---

## Questions to Expect

**Q: How did you select these 45 firms?**
> "I started with industry rankings, then filtered for firms with CAS offerings, evidence of technology adoption, and appropriate size. High-priority firms checked multiple boxes."

**Q: What would you do differently with more time?**
> "I'd add revenue estimates, track funding/acquisition news, and build alerts for when firms show new buying signals. I'd also integrate with LinkedIn Sales Navigator data."

**Q: How would you keep this updated?**
> "In production, I'd set up web scrapers for news alerts, LinkedIn job postings (hiring = growth signal), and industry publication mentions. The scoring could be refreshed automatically."

---

*Created by Jake McCorkle as part of the Deployed Intelligence project application for Basis.*
