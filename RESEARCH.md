# Basis Target Map - Research & Learnings

## About This Project
Building an interactive map/dashboard for a Basis job application showing CPA firms that would be ideal targets for Basis's AI platform.

---

## What Basis Actually Does

### Core Product
Basis provides **AI agents** (not chatbots) that perform real accounting work autonomously. Key distinction: they "do" work, not just "suggest" work.

### Specific Tasks Automated
| Task | Description |
|------|-------------|
| **Transaction Entry** | Automating data entry into ledgers |
| **Data Verification** | Checking accuracy of entered data |
| **Bank Reconciliations** | Matching payables with cash that left the bank |
| **Journal Entries** | Preparing entries with full explanations of logic, data sources, and confidence levels |
| **Financial Summaries** | Creating summary reports |

### Primary Practice Area: Client Accounting Services (CAS)

**What is CAS?**
CAS = Client Accounting Services = **outsourced bookkeeping**

Instead of a small business hiring their own in-house accountant, they pay a CPA firm to handle day-to-day accounting:
- Recording transactions
- Paying bills
- Reconciling bank statements
- Preparing monthly financial reports
- Payroll processing

**Why CAS is Basis's sweet spot:**
| Service Type | Characteristics | AI-Ready? |
|--------------|-----------------|-----------|
| **Tax** | Seasonal, complex, judgment-heavy | Not yet |
| **Audit** | Investigative, requires skepticism | Not yet |
| **CAS** | Routine, repeatable, process-driven | **Yes!** |

CAS work is high-volume and follows clear rules - perfect for AI automation. A firm might have 50+ small business clients each needing the same tasks monthly.

### Integrations
- QuickBooks
- Xero
- Existing ledger systems and file systems

---

## Key Metrics & Results

| Metric | Value | Source |
|--------|-------|--------|
| Time savings | **Up to 30%** | Wiss partnership announcement |
| Accuracy | "Extremely high" | Paul Ursich, Wiss Partner |
| Adoption | "Rapidly increasing month-over-month" | Wiss case study |

---

## The Wiss Case Study (Basis's Flagship Customer)

### Wiss Profile
- **Location:** Florham Park, NJ
- **Size:** ~450 accountants
- **Ranking:** Top 100 CPA firm
- **Started with Basis:** November 2023 (beta)
- **Full deployment:** September 2024

### What Wiss Said
> "Basis offers a unique capability to fully automate accounting workflows with extremely high accuracy in a way that not only frees up our team but drives the bottom line."
> — Paul Ursich, Partner

> "Basis is a game-changer because, unlike normal automation, it can truly understand the work it's performing and adjust to different situations."
> — Mike Castle, Partner

### Why Wiss Adopted Basis
1. Reduce manual work in CAS practice
2. Scale CAS service line without proportional headcount
3. Free up staff for higher-value advisory work
4. Improve work-life balance for accountants
5. Drive profitability

---

## Founder Insights (from Podcasts & Interviews)

### The Founders

| Name | Role | Background |
|------|------|------------|
| **Matt Harpe** | Co-Founder & CEO | Former Boston Consulting Group, Softbank |
| **Mitchell Troyanovsky** | Co-Founder | Technical co-founder |

### Podcast Appearances

**1. Future Finance Podcast (May 2024)**
- Guest: Mitchell Troyanovsky
- Host: Paul Barnhurst & Glenn Hopper
- Topics: AI automation in accounting, balance between automation and human expertise
- [QFlow Blog Summary](https://blog.qflow.ai/post/future-finance-podcast-mitchell-troyanovsky/)

**2. Business Beyond Borders Podcast**
- Guest: Matt Harpe
- Episode: "Revolutionizing Accounting: The Future of Automation with Basis"
- Topics: How Basis transforms traditional accounting, benefits of automation, future outlook
- [Listen on Podbean](https://businessbeyondborders.podbean.com/e/revolutionizing-accounting-the-future-of-automation-with-basis/)

### Key Founder Quotes

> "Accounting is the language companies use to understand their business and make decisions. It's a critical part of our market economy and often underappreciated. Basis will give every accountant a team of AI assistants – to transform not just their practice, but to enable teams far beyond accounting to function more efficiently and effectively."
> — Mitchell Troyanovsky, Co-Founder

> [On AI agents] "They're like juniors on the team, capable of entering transactions, validating data, and reporting results—tasks that traditionally consume significant hours for firms managing hundreds of accounts."
> — Matt Harpe, CEO ([Maginative, Dec 2024](https://www.maginative.com/article/basis-secures-34m-to-deploy-ai-agents-for-accounting-firms/))

> "This technology is a new paradigm for accounting. Learning to work with your computer, not just on it, might be an even bigger shift than going from paper to digital. Over the last year, as accountants have experienced what's possible with the most cutting-edge AI, we've seen more and more firms decide that AI must become the top strategic priority."
> — Mitchell Troyanovsky, Co-Founder ([Accounting Today, Dec 2024](https://www.accountingtoday.com/news/major-ai-players-back-basis-with-34-million-series-a))

> "We're putting every dollar back into the platform and team — to invest in ML research, to continue to bring the most cutting-edge AI to accounting firms, and to open additional slots for firms."
> — Matt Harpe, CEO

### Insights from Matt Harpe's Background

The concept of Basis was born when Harpe was exposed to the accounting world while working at BCG:
- He was tasked with finding ways to optimize business processes
- He discovered how rare it was for organizations to leverage granular accounting data in decision-making
- This insight led to the realization that accounting itself needed to be transformed before the data could be useful

---

## Basis Company Info

### Funding
- **Series A:** $34M (December 2024)
- **Lead investor:** Khosla Ventures
- **Notable investors:** Nat Friedman, Daniel Gross, Larry Summers, Adam D'Angelo
- **Seed:** $3.6M from Better Tomorrow Ventures, BoxGroup, Avid Ventures

### Technology
- Powered by OpenAI models (o3, o3-Pro, GPT-4.1, GPT-5)
- Uses function calling for multi-step workflow completion
- Agents share context through central layer for transparency

### Business Model
- Sells directly to accounting firms
- Positions as "collaborator, not competitor"
- Currently targeting Top 100 firms
- Waitlist model (not widely available)

---

## Ideal Target Firm Profile

Based on Wiss as the benchmark, ideal Basis targets are:

### Firm Characteristics
- [ ] **Size:** 200-5,000+ employees (enough volume to benefit from automation)
- [ ] **Has CAS Practice:** Must offer client accounting services
- [ ] **Tech-Forward Culture:** History of adopting new technology
- [ ] **Growth-Oriented:** Looking to scale without linear headcount growth
- [ ] **Regional/National:** Large enough to have budget for enterprise software

### Why These Firms Would Buy
1. **Labor shortage** - Hard to hire accountants, AI fills gaps
2. **Margin pressure** - Automation improves profitability
3. **Scale ambitions** - Want to grow CAS without proportional hiring
4. **Competitive pressure** - Don't want to fall behind peers using AI
5. **Staff retention** - Better work-life balance = less turnover

---

## Opportunity Sizing Logic

### How to Estimate $ Opportunity per Firm

**Approach 1: Based on CAS Revenue**
- Estimate CAS as ~15-25% of total firm revenue
- Basis likely charges based on usage/seats in CAS practice
- If 30% time savings → significant ROI justification

**Approach 2: Based on Employee Count**
- Estimate CAS headcount as ~20% of total firm
- Price per CAS accountant seat × number of CAS staff

**Approach 3: Revenue-Based SaaS Pricing**
- Enterprise SaaS typically 0.1-0.5% of customer revenue
- For a $100M firm → $100K-$500K annual contract

*Note: Actual Basis pricing is not public. These are estimates for demonstration.*

---

## Sources

### About Basis (Product & Company)
| Source | What It Tells Us |
|--------|------------------|
| [Basis AI Official Site](https://www.getbasis.ai/) | Product overview, positioning |
| [OpenAI Case Study on Basis](https://openai.com/index/basis/) | Technical details on AI agents, how they built it |
| [Basis About Page](https://www.getbasis.ai/about) | Team, mission, company background |

### Funding & Business
| Source | What It Tells Us |
|--------|------------------|
| [Maginative - Basis $34M Funding](https://www.maginative.com/article/basis-secures-34m-to-deploy-ai-agents-for-accounting-firms/) | Series A details, investor list |
| [The Finance Story - Khosla Investment](https://thefinancestory.com/basis-raised-34mn-building-ai-agents-for-accountants) | Funding context, market opportunity |
| [Crunchbase - Basis Profile](https://www.crunchbase.com/organization/basis-d271) | Funding history, company data |

### Wiss Partnership (Key Case Study)
| Source | What It Tells Us |
|--------|------------------|
| [Wiss Official Announcement](https://wiss.com/wiss-announces-strategic-partnership-with-accounting-ai-platform-basis/) | Partnership details, quotes from partners |
| [CPA Practice Advisor Coverage](https://www.cpapracticeadvisor.com/2024/09/13/wiss-enters-strategic-partnership-with-ai-platform-basis/110481/) | Industry perspective on the deal |
| [NJ Business Magazine](https://njbmagazine.com/njb-news-now/wiss-and-basis-enter-strategic-ai-partnership/) | Local business coverage |

### Industry Context
| Source | What It Tells Us |
|--------|------------------|
| [Journal of Accountancy - AI for CAS](https://www.journalofaccountancy.com/issues/2026/jan/simple-but-effective-ai-use-cases-for-cas/) | How CAS practices are using AI |
| [a16z - AI in Accounting](https://a16z.com/generative-ai-in-accounting/) | VC perspective on AI accounting opportunity |
| [AIMultiple - Top Accounting AI Agents](https://research.aimultiple.com/accounting-ai-agent/) | Competitive landscape |
| [AI Expert Network - Basis Profile](https://aiexpert.network/basis/) | Third-party product analysis |

---

## Known Customers

| Status | Firm | Details |
|--------|------|---------|
| **Confirmed** | Wiss & Company | Only publicly named customer. Partnership announced Sept 2024. |
| **Unconfirmed** | "Select Top 100 firms" | Basis claims to work with multiple Top 100 firms but doesn't name them |
| **Investors** | Several accounting firms | Invested in seed round - may also be customers |

**Why only one public customer?** Common for early-stage enterprise B2B:
- Customer NDAs
- Firms don't want competitors knowing they use AI
- Basis still in early growth phase (founded 2023)

---

## What Accountants Do With Time Savings

Basis frees up ~30% of CAS staff time. Firms redirect this toward:

| Instead of... | They now do... |
|---------------|----------------|
| Data entry | **Client advisory** - strategic financial guidance |
| Reconciling transactions | **Business development** - winning new clients |
| Manual verification | **Higher-margin services** - CFO-as-a-service, forecasting |
| Repetitive bookkeeping | **Relationship building** - deeper client conversations |

**Business case:** CAS = low-margin, high-volume. Advisory = high-margin. Firms shift revenue mix toward profitability.

---

## The Training Question (Unresolved Industry Issue)

**Concern:** If AI handles fundamental tasks, how do junior accountants learn?

**Possible answers:**
1. AI as teaching tool - juniors review AI's work and explanations
2. Supervised learning - seniors approve AI output, creating teaching moments
3. Training modes - some firms keep manual processes for education
4. Role evolution - "fundamentals" shift from data entry to data interpretation

**Honest take:** This is genuinely unresolved. Good interview discussion topic.

---

## Open Questions & Interview Topics

### About Basis (Product & Business)
| Question | Status | Notes |
|----------|--------|-------|
| What is Basis's actual pricing model? | Unanswered | Not public. Likely per-seat or usage-based. |
| Which firms are currently Basis customers? | Partial | Only Wiss is public. Claims "select Top 100 firms." |
| What are the main competitors to Basis? | To research | Botkeeper? Vic.ai? Internal solutions? |
| How does Basis handle data security/client confidentiality? | Unanswered | Critical for accounting - SOC 2 compliance? |
| What happens when AI makes mistakes on client work? | Unanswered | Liability, error correction, audit trails? |

### About the Market
| Question | Status | Notes |
|----------|--------|-------|
| How large is the CAS market overall? | To research | Growing 16% annually per AICPA |
| What's the typical sales cycle for enterprise accounting software? | Unanswered | Likely 3-12 months for Top 100 firms |
| Why are firms hesitant to publicly announce AI adoption? | Answered | NDAs, competitive concerns, client perception |
| What % of Top 100 firms have dedicated CAS practices? | To research | Would help prioritize targets |

### Strategic/Thoughtful Questions (Good for Interviews)
| Question | Status | Notes |
|----------|--------|-------|
| What do accountants do with the time Basis frees up? | Answered | Advisory, biz dev, client relationships |
| How will entry-level accountants learn fundamentals if AI handles basic tasks? | Discussed | Unresolved industry issue - good interview topic |
| Will AI commoditize CAS services and drive down prices? | Unanswered | If everyone automates, does the advantage disappear? |
| How do firms measure ROI on Basis? | Unanswered | Time savings × hourly rate? New capacity? |
| What's the change management challenge? | Unanswered | Getting accountants to trust and adopt AI |
| Could Basis expand beyond CAS to audit/tax? | Unanswered | Product roadmap question |

### Questions That Arose During This Project
| Question | Context |
|----------|---------|
| How should opportunity $ be calculated? | We used: Est. CAS Staff (18% of total) × $5K/seat/year |
| What makes a firm "high priority" vs "medium"? | CAS focus + tech culture + right size (300-5000 employees) |
| Why include Big 4 as "low priority"? | They build internally, unlikely to buy from startups |

---

## Design Inspiration

User mentioned [Situation.watch](https://www.situation.watch/) as inspiration:
- OSINT/intelligence dashboard aesthetic
- Dark theme, "command center" vibe
- Real-time data feel
- Data-dense visualizations

---

*Last updated: January 2026*
