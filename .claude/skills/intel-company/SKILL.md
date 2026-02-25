---
name: intel-company
description: >
  McKinsey-style AI consulting skill that generates an interactive HTML dashboard
  for company analysis and AI use case identification. Input a company name and meeting
  context (e.g., "Prepare AI consulting pitch for Novartis, meeting with CTO about AI transformation")
  to receive a comprehensive 8-tab strategic dashboard featuring executive summaries,
  competitive analysis, industry trends, AI maturity assessments, and 8 prioritized
  AI use cases positioned across the Strategy-Assessment-Pilot-Scale-Operate maturity curve.
  Use this skill for: executive consulting preparation, AI transformation strategy,
  use case identification, competitive benchmarking, market entry analysis, and
  C-suite pitch preparation.
---

# Intel Company - AI Strategy Dashboard

## CRITICAL: TEMPLATE AND ASSETS LOCATION

**BEFORE generating any report, you MUST:**

1. **Find the template** using Glob:
   ```
   Glob pattern: **/intel-company/report-template.html
   ```

2. **Find the output directory** using Glob:
   ```
   Glob pattern: **/intel-company/assets/
   ```
   The output directory is the PARENT of the assets folder (where `assets/` lives).

3. **Verify assets exist**: The `assets/` folder must contain:
   - `artifact-logo-horizontal.png` (header logo)
   - `artifact-logo-vertical.png` (alternate logo)

**The HTML template uses relative paths to assets (`assets/artifact-logo-horizontal.png`), so the generated report MUST be saved in the same directory as the `assets/` folder.**

## CRITICAL: COMPANY LOGO

The template supports dynamic company logos in the header. When generating a report:

1. **Search for the company logo** using WebSearch: `{{COMPANY_NAME}} logo png transparent`
2. **Use the logo URL** as `{{COMPANY_LOGO_URL}}` in the header `<img>` tag
3. The template includes a fallback: if the logo fails to load (`onerror`), it displays the company initials (`{{COMPANY_INITIALS}}`) in a styled circle instead
4. **Prefer official/high-quality logos** from company websites, Wikipedia, or brand asset pages
5. Use `clearbit.com/logo/{{company-domain}}` as a reliable fallback source (e.g., `https://logo.clearbit.com/novartis.com`)

## CRITICAL: AI READINESS GAUGE CHART

The gauge chart uses CSS `conic-gradient` via a CSS custom property `--gauge-percentage`. When rendering:
- Set the percentage as a CSS variable: `style="--gauge-percentage: 72"` (for 72%)
- The value is 0-100 representing the AI readiness score as a percentage (score * 10)
- Example: AI readiness score of 6.5 → `--gauge-percentage: 65`

## CRITICAL: METHODOLOGY INFO BOXES

**Every single card on every tab** must have a methodology callout (inline info badge). The format is:
```html
<span class="methodology-callout">
    <span class="methodology-icon">ℹ️</span> How calculated
    <div class="methodology-tooltip">DETAILED explanation of data sources, methodology, confidence level, and any caveats for this specific section.</div>
</span>
```
The tooltip text must be **specific to each section** - never use generic text. Explain:
- What data sources were used (e.g., "SEC 10-K filings", "LinkedIn job postings", "Gartner Magic Quadrant 2024")
- How the analysis was derived (e.g., "Scored based on 6-dimension maturity model")
- Confidence level (e.g., "VERIFIED from public filings" vs "INFERRED from job postings")
- Any limitations (e.g., "Private company - limited financial data available")

## CRITICAL: SOURCE LINKS MUST BE CLICKABLE

**Every source in the Sources section MUST be a clickable link with an actual URL.**

During research, you MUST track the actual URLs of every source you use.

## OUTPUT FORMAT

**OUTPUT: Single-file HTML dashboard saved alongside the `assets/` folder**

This skill creates an **HTML file** (not Word, not DOCX, not PDF). The output is:
1. A `.html` file written using the `Write` tool
2. Saved in the same directory as `assets/` folder
3. Deployed to GitHub Pages via `Bash` git commands
4. Opened locally with `open` command

## ALLOWED TOOLS - USE ONLY THESE

1. `Glob` - find the template and output directory
2. `WebSearch` - research the company (run 25-35 searches)
3. `Read` - read the template file
4. `Write` - save the final HTML to the output directory
5. `Bash` - git commands and `open` command only

## FORBIDDEN TOOLS - NEVER USE

- Any tool starting with `mcp__`
- Browser tools
- Chrome extension tools
- Document creation tools
- Shortcuts or workflows

## Overview

The AI Strategy Dashboard is a comprehensive consulting tool designed for enterprise AI strategy development and executive engagement preparation. It transforms a company name and meeting context into an interactive, data-driven HTML dashboard that delivers McKinsey-grade analysis across eight strategic dimensions.

**Core Purpose:** Enable rapid preparation of AI consulting pitches, competitive analysis, and strategic recommendations with verifiable research, transparent methodology, and actionable AI use case identification.

**Output Deliverable:** A single-page HTML dashboard with 8 tabbed sections, embedded charts, source attribution, and methodology transparency—ready for executive presentation or internal strategy work.

---

## Execution Workflow

The skill follows a structured 5-phase process optimized for research depth and analysis quality:

### Phase 1: Parse Input
Extract and validate user input to establish research parameters and meeting context.

**Input Format Examples:**
- "Prepare AI consulting pitch for Apple, C-suite presentation on enterprise AI roadmap"
- "AI strategy analysis for Pfizer, meeting with VP of R&D about clinical trials automation"
- "Competitive AI strategy brief for JPMorgan Chase, internal board meeting prep"

**Extracted Parameters:**
- `{{COMPANY_NAME}}` - Target company for analysis
- `{{MEETING_CONTEXT}}` - Role, department, and strategic focus
- `{{SECRET_TOKEN}}` - 8-character random token for unique URL (generated automatically)

### Phase 2: Research (25-35 Web Searches)

Conduct systematic web research organized into 6 search clusters. Each search is executed sequentially with WebSearch tool, results parsed, and URLs stored for source attribution.

#### Cluster 1: Company Profile (5 searches)
1. `{{COMPANY_NAME}} about history overview`
2. `{{COMPANY_NAME}} annual report revenue financials [year]`
3. `{{COMPANY_NAME}} CEO leadership team executives`
4. `{{COMPANY_NAME}} products services business model`
5. `{{COMPANY_NAME}} technology stack digital transformation`

#### Cluster 2: Competitive Intelligence (5 searches)
6. `{{COMPANY_NAME}} competitors market share`
7. `{{COMPANY_NAME}} vs [identified_competitor] comparison`
8. `{{COMPANY_NAME}} competitive advantage differentiation`
9. `{{COMPANY_NAME}} industry market size [year]`
10. `{{COMPANY_NAME}} market position ranking`

#### Cluster 3: AI & Digital Strategy (5 searches)
11. `{{COMPANY_NAME}} AI artificial intelligence strategy`
12. `{{COMPANY_NAME}} digital transformation initiatives`
13. `{{COMPANY_NAME}} AI use cases machine learning`
14. `{{COMPANY_NAME}} data analytics infrastructure`
15. `{{COMPANY_NAME}} AI hiring jobs machine learning engineer`

#### Cluster 4: Industry & Trends (5 searches)
16. `[IDENTIFIED_INDUSTRY] AI trends 2025`
17. `[IDENTIFIED_INDUSTRY] digital disruption technology`
18. `[IDENTIFIED_INDUSTRY] regulatory AI governance`
19. `[IDENTIFIED_INDUSTRY] market outlook forecast`
20. `{{COMPANY_NAME}} innovation R&D patents`

#### Cluster 5: Recent Developments (5 searches)
21. `{{COMPANY_NAME}} news announcements 2024 2025`
22. `{{COMPANY_NAME}} partnerships acquisitions 2024 2025`
23. `{{COMPANY_NAME}} earnings quarterly results`
24. `{{COMPANY_NAME}} strategy outlook priorities`
25. `{{COMPANY_NAME}} challenges risks issues`

#### Cluster 6: Meeting Context Specific (3-5 searches)
26-30. Role-specific searches dynamically generated based on {{MEETING_CONTEXT}}
- If meeting with CTO: "{{COMPANY_NAME}} technology priorities cloud infrastructure"
- If meeting with CFO: "{{COMPANY_NAME}} cost reduction efficiency initiatives"
- If meeting with Chief Strategy: "{{COMPANY_NAME}} portfolio transformation strategic priorities"

**Research Execution Rules:**
- Each search stored with timestamp and URL for source tracking
- Results reviewed for relevance (include top 5-10 results per search)
- Company logos, CEO photos, and organizational charts collected where available
- No more than 30 searches unless additional context requires deeper analysis

### Phase 3: Synthesize & Analyze

Aggregate research findings into structured analysis using prescribed frameworks:

#### Framework 1: AI Maturity Model (6 Dimensions, 1-5 Scale)
Each dimension scored with evidence-based reasoning:

1. **Strategy:** Does company have defined AI strategy, governance model, and executive sponsorship?
2. **Data:** Quality of data infrastructure, governance, accessibility, and volume
3. **Technology:** Modern cloud/ML platforms, MLOps maturity, scalability
4. **Talent:** AI hiring, retention, upskilling programs, academic partnerships
5. **Culture:** Innovation metrics (patents, hackathons, R&D spend %), risk tolerance
6. **Governance:** Ethics frameworks, bias monitoring, regulatory compliance

Scores assigned with confidence levels (VERIFIED, INFERRED, SPECULATIVE) and cited evidence.

#### Framework 2: Porter's Five Forces (Lite)
- **Supplier Power:** Critical vendors, switching costs
- **Buyer Power:** Customer concentration, pricing power
- **Threat of New Entrants:** Barriers to entry, capital requirements
- **Threat of Substitutes:** Direct alternatives, technology disruption
- **Competitive Rivalry:** Intensity, differentiation, consolidation

#### Framework 3: SWOT Analysis
- **Strengths:** Unique advantages, market position, resources
- **Weaknesses:** Operational gaps, talent deficits, legacy systems
- **Opportunities:** AI-addressable pain points, untapped markets, emerging trends
- **Threats:** Disruption risks, competitive moves, regulatory changes

#### Framework 4: Impact vs Effort Matrix
All 8 AI use cases positioned on 2x2 matrix:
- X-axis: Implementation Complexity (Low/Medium/High)
- Y-axis: Expected Business Impact (Low/Medium/High)
- Quadrants define: Quick Wins, Strategic Investments, Time Sinks, Future Opportunities

#### Framework 5: McKinsey 3 Horizons
Classify each use case into transformation timeline:
- **Horizon 1 (0-12 months):** Quick wins delivering immediate value
- **Horizon 2 (1-3 years):** Core transformation initiatives
- **Horizon 3 (3+ years):** Disruptive, transformational investments

### Phase 4: Generate Dashboard HTML

Transform synthesized analysis into interactive 8-tab dashboard using report-template.html and component templates.

**Dashboard Tabs (8 Total):**

#### Tab 1: Executive Summary
- Company snapshot widget (name, industry, HQ, size, revenue, CEO)
- AI Readiness Score (1-10) with methodology tooltip
- Digital Maturity Rating (1-10)
- Key Findings (3-5 bullet insights)
- Top 3 AI Opportunities Preview (from Tab 6)
- Meeting Fit Score (1-10) based on meeting context
- Confidence level indicators

#### Tab 2: Company Deep Dive
- Business Model Analysis (revenue streams, value proposition, customer segments)
- Financial Performance (5-year revenue trend, R&D spending, EBITDA margin)
- Technology Stack Signals (identified platforms, cloud providers, tech maturity)
- Strategic Priorities (from annual reports, earnings calls, investor presentations)
- Recent Announcements (last 6-12 months with dates and impact assessment)
- Organizational Structure (divisions, reported AI centers of excellence, key roles)
- Growth Trajectory (historical and projected)

#### Tab 3: Competitive Landscape
- Key Competitors (5-8 identified with reasoning why they matter)
- Competitive Positioning Matrix (scatter plot: innovation vs market share)
- Competitive Advantages & Moat Analysis (defensibility assessment)
- Competitor AI Adoption Comparison (table with implementation scores)
- Market Share Estimates (with confidence levels)
- Differentiation Analysis (vs 2-3 key competitors)
- Disruption Risk from Non-Traditional Players
- **NEW: Competitive AI Comparison Summary** - Overall assessment of how {{COMPANY_NAME}} compares to competitors in AI. Are they ahead, behind, or on par? Be specific and cite evidence.
- **NEW: Competitor AI Initiatives Detail** - For each major competitor, list their specific AI initiatives, products, and investments. Use `competitor-ai-detail` cards. The more concrete the better (product names, investment amounts, partnerships).
- **NEW: AI Maturity vs AI Ambition Chart** - Scatter plot with all competitors AND the subject company. X-axis = current AI maturity (what they've done). Y-axis = AI ambition (what they've announced/planned). Subject company uses `subject-company` class. Include tooltip text explaining positioning rationale for each company.

#### Tab 4: Market & Industry Analysis
- Industry Overview & Market Size (with growth rate, TAM)
- Key Industry Trends (5-7 identified with 5-year impact assessment)
- Disruption Forces (technology, regulation, new entrants, business model shifts)
- Value Chain Analysis (where company sits, power dynamics)
- Industry-Specific AI Adoption Trends (benchmarking data)
- Regulatory Landscape (relevant AI regulations, compliance requirements, emerging policy)
- Consolidation & M&A Activity (if relevant)

#### Tab 5: Digital & AI Maturity Assessment
- **NEW: AI Journey Summary** (FIRST card in this tab) - Two-column layout:
  - Left: "Confirmed AI Implementations" (insight-box success) - What the company has ACTUALLY done in AI (deployed products, tools, teams). Use {{AI_CONFIRMED_IMPLEMENTATIONS}}.
  - Right: "Announced AI Plans & Ambitions" (insight-box warning) - What they've publicly announced or signaled for the future. Use {{AI_ANNOUNCED_PLANS}}.
- AI Maturity Scorecard (6-dimension radar chart - ensure it renders centered with max-width 450px)
- Current Digital Capabilities (cloud migration %, digital customer %, omnichannel presence)
- Technology Readiness Indicators (infrastructure quality, data governance, API maturity)
- Data Infrastructure Signals (data lake/warehouse presence, data science team size)
- AI Talent Indicators (identified ML engineers, data scientists from job postings)
- Innovation Culture Signals (patents filed, R&D % of revenue, hackathon participation)
- Peer Benchmarking (vs industry average on each maturity dimension)
- Historical Progress (year-over-year improvement trajectory if available)

#### Tab 6: Top 8 AI Use Cases
For each of 8 prioritized use cases:
- **Title & Description:** Clear problem statement and solution approach
- **Business Area:** Function affected (Operations, Sales, R&D, Customer Service, Supply Chain, Finance, HR, etc.)
- **Maturity Stage:** Position on Strategy → Assessment → Pilot → Scale → Operate curve
- **Expected Business Impact:** High/Medium/Low with specific reasoning (cost savings %, revenue %, efficiency gain %)
- **Implementation Complexity:** High/Medium/Low (infrastructure, data, talent, change management factors)
- **Why This Company:** 2-3 sentence explanation why this use case fits this specific company
- **Quick Win vs Transformation:** Horizon classification (1/2/3) and timeline (weeks/months/quarters)
- **Estimated Timeline:** Implementation duration from project start to full scale
- **Risk Factors:** Key implementation risks and mitigation approaches

Additional visualization:
- **NEW: Impact vs Feasibility Matrix (2x2):** All 8 use cases plotted as numbered dots on a centered chart. X-axis = Feasibility (Low→High). Y-axis = Business Impact (Low→High). Quadrants: "Strategic Bets" (top-left), "Quick Wins" (top-right), "Deprioritize" (bottom-left), "Low-Hanging Fruit" (bottom-right). Use `ifm-dot` CSS class with `ifm-dot-tooltip` for hover labels. Use {{IFM_DOTS}} and {{IFM_LEGEND}} placeholders.
- Maturity Curve Chart: All 8 use cases plotted on horizontal strategy → operate axis
- Value Realization Timeline: Gantt-style view of implementation phases across all use cases
- **NEW: Competitor Benchmarks section** - After the 8 use case cards, add a card titled "Competitor Benchmarks: Who Has Done What?" with {{USE_CASE_COMPETITOR_BENCHMARKS}}. For each use case, describe what competitors have already implemented in similar areas. Be as concrete as possible (product names, results achieved, timelines).

#### Tab 7: Engagement Strategy
- Meeting Preparation Brief (key talking points, agenda sequencing)
- Value Proposition Framing (how AI strategy drives company's specific business outcomes)
- Key Talking Points (5-7 specific callouts aligned to identified priorities)
- Anticipated Objections & Responses (likely concerns with prepared rebuttals)
- Recommended Approach (conversation flow, discussion sequence, stakeholder handling)
- Next Steps Proposal (concrete deliverables, timeline for detailed roadmap)
- Topics to Avoid (sensitivities, competitive vulnerabilities, internal politics if known)

#### Tab 8: Sources & Methodology
- Complete Source List (all 25-35 searches with clickable URLs)
- Confidence Levels per Section (VERIFIED / INFERRED / SPECULATIVE badges)
- Data Freshness Indicators (latest search date, source recency)
- Methodology Transparency Notes:
  - AI Maturity Model: 6-dimension framework explanation
  - Porter's Five Forces: Application to company's industry
  - Impact vs Effort: Scoring methodology and weighting
  - Source Collection: Web search approach and search strategy
  - Limitations: Known gaps, speculative sections, external factors

---

## Key Analysis Methodologies

### 1. AI Maturity Model (6 Dimensions, 1-5 Scale)

**Purpose:** Establish objective baseline of company's AI readiness across operational and organizational dimensions.

**Dimensions & Scoring:**

| Dimension | Level 1 | Level 2 | Level 3 | Level 4 | Level 5 |
|-----------|---------|---------|---------|---------|---------|
| **Strategy** | No AI strategy | Ad-hoc pilots | Defined roadmap | Integrated strategy | AI core to business model |
| **Data** | Fragmented, poor quality | Centralized warehouse | Data governance framework | Real-time analytics | Data monetization |
| **Technology** | Legacy systems | Cloud migration started | Modern ML stack | MLOps at scale | Cutting-edge AI infrastructure |
| **Talent** | Minimal AI hiring | Recruiting senior talent | Training programs | AI centers of excellence | Industry thought leaders |
| **Culture** | Risk averse | Innovation starting | Experimentation encouraged | Fail-fast mentality | AI-first culture |
| **Governance** | No AI ethics | Basic compliance | Documented frameworks | Automated monitoring | Industry leadership on AI ethics |

**Evidence Collection:**
- Job postings analyzed for AI talent hiring velocity
- Patent filings and publications tracked
- Press releases on AI investments reviewed
- Annual reports for R&D spending %
- Public statements from executives on AI priorities
- Analyst reports (Gartner, Forrester, McKinsey if available)

### 2. Porter's Five Forces (Adapted for AI Context)

**Application:** Understand structural industry attractiveness and AI's role in competitive positioning.

**Analysis Questions:**
- What specialized suppliers does this company depend on? (Cloud providers, chip manufacturers, data providers)
- How much buyer power does customer base have? Can they demand AI-enhanced products?
- What barriers to entry exist? (Talent, data, capital, regulatory)
- What substitutes threaten the business model? (Direct competitors, adjacent technologies, disruptive entrants)
- Who are the most intense competitors? What's their AI posture?

### 3. SWOT Framework

**Purpose:** Synthesize company positioning relative to AI transformation opportunity.

**Application:**
- Strengths: What competitive advantages support AI leadership? (Brand, data, talent, capital, customer relationships)
- Weaknesses: What gaps prevent AI adoption? (Legacy tech, talent scarcity, organizational silos, culture)
- Opportunities: What specific AI use cases could unlock value? (Market expansion, margin improvement, new revenue streams)
- Threats: What could disrupt the company's AI strategy? (Competitors ahead, talent exodus, regulatory backlash, commoditization)

### 4. Impact vs Effort Matrix

**Purpose:** Prioritize AI use cases for maximum strategic value and implementation feasibility.

**Axes:**
- **Y-axis (Impact):** Expected business value (revenue increase, cost reduction, customer satisfaction, risk mitigation)
- **X-axis (Effort):** Implementation complexity (infrastructure requirements, data needs, talent, change management, timeline)

**Quadrants:**
- **Quick Wins (High Impact, Low Effort):** Immediate candidates for Horizon 1 pilots
- **Strategic Bets (High Impact, High Effort):** Transformational opportunities requiring board-level commitment
- **Time Sinks (Low Impact, High Effort):** Avoid unless strategic (tech debt reduction, compliance)
- **Future Opportunities (Low Impact, Low Effort):** Low priority but monitor

### 5. McKinsey 3 Horizons

**Purpose:** Sequence AI investments across time horizons and strategic impact.

- **Horizon 1 (0-12 months):** Quick wins, proof-of-concept, build organizational confidence
- **Horizon 2 (1-3 years):** Core transformation initiatives, scaled pilots, capability building
- **Horizon 3 (3+ years):** Disruptive bets, new business models, competitive defense

---

## Use Case Development Framework

Each of the 8 AI use cases is developed using this structured approach:

### Use Case Components

**1. Problem Statement & Solution**
Clear description of current business challenge and how AI addresses it.

**2. Business Impact Quantification**
- Cost Reduction: Direct savings (labor, materials, errors, waste)
- Revenue Enhancement: New revenue streams, pricing power, customer satisfaction
- Risk Mitigation: Reduced downside, regulatory compliance, operational resilience
- Efficiency: Time savings, throughput increase, quality improvement

**Example:** "Predictive maintenance for manufacturing assets - reduces unplanned downtime by 40%, extends equipment life by 15%, ROI within 18 months"

**3. Implementation Complexity Assessment**
- Data Requirements: Availability, quality, historical depth
- Technical Infrastructure: Existing platforms, gaps, new investments
- Talent Requirements: Data scientists, ML engineers, domain experts needed
- Organizational Change: Process redesign, skill development, stakeholder management
- Timeline: Realistic phased implementation (months to scale)

**4. Company-Specific Fit**
Explain why this use case is particularly valuable for THIS company:
- Aligns with stated strategic priorities
- Addresses identified pain points
- Leverages existing capabilities
- Fits industry/customer dynamics
- Matches current digital maturity level

**5. Maturity Curve Positioning**
- Where is company on adoption curve? (Strategy phase? First pilots? Scaling?)
- What's the recommended next phase?
- What milestones indicate readiness for phase progression?

---

## Placeholder Reference Table

All {{PLACEHOLDERS}} used throughout execution:

| Placeholder | Description | Example | Source |
|------------|-------------|---------|--------|
| `{{COMPANY_NAME}}` | Target company for analysis | Apple, Novartis, JPMorgan | User input |
| `{{INDUSTRY}}` | Company's primary industry | Technology, Pharmaceuticals, Financial Services | Derived from company research |
| `{{MEETING_CONTEXT}}` | Strategic focus of engagement | "C-suite, AI transformation roadmap" | User input |
| `{{MEETING_ROLE}}` | Meeting attendee's function | CTO, CFO, Chief Strategy Officer | Derived from context |
| `{{SECRET_TOKEN}}` | 8-char unique URL token | a7k2q9mx | Generated (random) |
| `{{COMPANY_HQ}}` | Headquarters location | San Francisco, CA | Web search |
| `{{COMPANY_REVENUE}}` | Latest annual revenue | $2.3B (2024) | Public financials |
| `{{COMPANY_SIZE}}` | Employee count | 45,000 FTE | Company disclosures |
| `{{CEO_NAME}}` | Current CEO | Satya Nadella | Leadership page |
| `{{REVENUE_TREND_5Y}}` | Historical revenue growth | +12% CAGR (2019-2024) | Financial statements |
| `{{AI_READINESS_SCORE}}` | Overall AI maturity (1-10) | 7.2/10 | Model output |
| `{{COMPETITOR_1..N}}` | Key identified competitors | Microsoft, Google, Amazon | Market research |
| `{{MARKET_SIZE}}` | Industry TAM | $500B+ (2024) | Industry reports |
| `{{AI_MATURITY_[DIM]}}` | Dimension score (Strategy/Data/etc) | 3.5, 4.0, 2.5, etc | Model scoring |
| `{{USE_CASE_[N]_TITLE}}` | AI use case title | Predictive Maintenance | Analysis output |
| `{{USE_CASE_[N]_IMPACT}}` | Use case business impact | High / Medium / Low | Framework assessment |
| `{{COMPANY_LOGO_URL}}` | URL to company logo PNG | https://logo.clearbit.com/apple.com | Web search / Clearbit |
| `{{COMPANY_INITIALS}}` | Company initials fallback | AP, NV, JP | Derived from name |
| `{{AI_CONFIRMED_IMPLEMENTATIONS}}` | Confirmed AI deployments | HTML list of confirmed AI projects | Web research |
| `{{AI_ANNOUNCED_PLANS}}` | Announced AI plans | HTML list of announced AI intentions | Web research |
| `{{COMPETITIVE_AI_SUMMARY}}` | Overall competitive AI assessment | Narrative comparing company vs peers | Analysis |
| `{{COMPETITOR_AI_DETAILS}}` | Detailed competitor AI initiatives | HTML cards per competitor with AI details | Web research |
| `{{AI_MATURITY_AMBITION_DOTS}}` | Scatter dots for AI maturity vs ambition chart | ai-scatter-dot elements | Analysis |
| `{{AI_MATURITY_AMBITION_LEGEND}}` | Legend for AI maturity vs ambition chart | Legend items with colors | Analysis |
| `{{IFM_DOTS}}` | Impact vs Feasibility matrix dots | ifm-dot elements with tooltips | Analysis |
| `{{IFM_LEGEND}}` | Legend for Impact vs Feasibility matrix | Numbered legend items | Analysis |
| `{{USE_CASE_COMPETITOR_BENCHMARKS}}` | What competitors have done for each use case | HTML sections per use case | Web research |
| `{{ORIGINAL_PROMPT}}` | User's original input prompt | "Prepare AI strategy for Novartis..." | User input |
| `{{REQUESTOR_NAME}}` | Name of person who requested the report | Marcel Wegmueller | User input / default |

---

## HTML Dashboard Components

The dashboard is built from a modular template system. Key components:

### Header Component
```html
<header class="dashboard-header">
  <div class="header-logo">
    <img src="assets/artifact-logo-horizontal.png" alt="Artifact" class="logo">
  </div>
  <div class="header-title">
    <h1>AI Strategy Dashboard: {{COMPANY_NAME}}</h1>
    <p class="subtitle">McKinsey-style AI Consulting Analysis</p>
  </div>
  <div class="header-meta">
    <span class="timestamp">Generated: {{GENERATION_TIMESTAMP}}</span>
    <span class="confidence-disclaimer">Based on {{TOTAL_SOURCES}} verified sources</span>
  </div>
</header>
```

### Tab Navigation Component
```html
<nav class="tab-navigation">
  <button class="tab-button active" data-tab="executive-summary">Executive Summary</button>
  <button class="tab-button" data-tab="company-deep-dive">Company Deep Dive</button>
  <button class="tab-button" data-tab="competitive-landscape">Competitive Landscape</button>
  <button class="tab-button" data-tab="market-analysis">Market & Industry</button>
  <button class="tab-button" data-tab="maturity-assessment">AI Maturity</button>
  <button class="tab-button" data-tab="use-cases">AI Use Cases</button>
  <button class="tab-button" data-tab="engagement-strategy">Engagement Strategy</button>
  <button class="tab-button" data-tab="sources">Sources & Methodology</button>
</nav>
```

### Methodology Callout Component (Used in Every Section)
```html
<div class="methodology-callout">
  <span class="methodology-icon" title="Based on Porter's Five Forces analysis of industry structure">ℹ️</span>
  <span class="methodology-text">Analysis based on Porter's Five Forces model of industry competitive dynamics</span>
</div>
```

### Source Confidence Badge Component
```html
<span class="confidence-badge verified">VERIFIED</span>  <!-- Data from public disclosures -->
<span class="confidence-badge inferred">INFERRED</span>   <!-- Derived from multiple sources -->
<span class="confidence-badge speculative">SPECULATIVE</span> <!-- Based on limited information -->
```

### Clickable Source Link Component
```html
<a href="{{SOURCE_URL}}" class="source-link" target="_blank">
  {{SOURCE_TITLE}} <span class="source-date">({{PUBLICATION_DATE}})</span>
</a>
```

### Maturity Curve Chart Component
HTML5 Canvas or SVG chart showing all 8 use cases positioned across:
Strategy → Assessment → Pilot → Scale → Operate

Color coding:
- Green: Quick wins (Horizon 1)
- Blue: Strategic initiatives (Horizon 2)
- Purple: Transformational (Horizon 3)

### Impact vs Effort Matrix Component
2x2 quadrant chart with use cases plotted by Impact (Y) vs Effort (X):
- Bubble size proportional to timeline (months)
- Color by Horizon (1/2/3)
- Interactive tooltips with use case details

### AI Maturity Radar Chart Component
6-dimensional radar chart showing company score on:
Strategy, Data, Technology, Talent, Culture, Governance
(Overlaid with industry average for benchmarking)

### Competitive Positioning Matrix Component
Scatter plot with Innovation (Y-axis) vs Market Share (X-axis):
- Bubble size represents revenue
- Company highlighted in primary color
- Competitors labeled and positioned

---

## CSS & Styling Conventions

### Color Palette
```css
/* Brand Colors */
--primary-blue: #0066CC;
--accent-green: #4CAF50;
--accent-orange: #FF9800;
--accent-purple: #9C27B0;
--neutral-gray: #F5F5F5;
--text-dark: #212121;
--text-light: #666666;

/* Horizon Colors */
--horizon-1-color: #4CAF50;  /* Quick wins (green) */
--horizon-2-color: #0066CC;  /* Strategic (blue) */
--horizon-3-color: #9C27B0;  /* Transformational (purple) */

/* Confidence Badge Colors */
--verified-color: #4CAF50;
--inferred-color: #FF9800;
--speculative-color: #F44336;
```

### Typography
- Headers: Inter or system font, bold
- Body: Arial/Segoe UI, 14px
- Code/Data: Monospace font, 12px
- All text dark gray (#212121) on white backgrounds

### Layout Rules
- Tab content: max-width 1200px, centered
- Padding: 24px margins inside tabs
- Charts: Responsive, 100% width up to 1200px
- Tables: Full width, striped rows
- Source links: Underlined, blue (#0066CC)

---

## Dashboard Generation & Deployment

### Step 1: Generate Unique Report Token
```bash
date +%s | shasum | head -c 8
```
Store this 8-character token as `{{SECRET_TOKEN}}`.

### Step 2: Read the Template
Read the template file found in the CRITICAL section above using the Read tool.

### Step 3: Create the HTML Content
- Replace all `{{PLACEHOLDER}}` values with researched data
- **PRESERVE all methodology callouts** - update their tooltip text with actual methodology
- **Use actual URLs** for all source items (as `<a href>` tags)
- No external chart library dependencies - all charts are CSS/SVG based

### Step 4: Create Filename
Format: `{company-name}-{token}.html` (lowercase, hyphens)
Example: `novartis-8cea1670.html`

### Step 5: Save the Report (use Write tool - NOT Bash)
Write to: `{OUTPUT_DIR}/{filename}.html`
**IMPORTANT**: Must be in same directory as `assets/` folder for logos to display.

### Step 6: Deploy to GitHub Pages (use Bash tool - MANDATORY)

**This step is NOT optional. Every generated dashboard MUST be automatically committed and pushed to GitHub Pages.**

Run these commands sequentially in a single Bash call:
```bash
cd {OUTPUT_DIR} && git add -A && git commit -m "Add AI strategy dashboard: {COMPANY_NAME}" && git push origin main
```

If git push fails due to authentication, inform the user but still proceed with opening locally.

### Step 7: Open Locally (use Bash tool)
```bash
open {OUTPUT_DIR}/{filename}.html
```

### Step 8: Return the Shareable URL

**Always display the GitHub Pages URL to the user after deployment:**

`https://mwegmueller.github.io/intel-company/{filename}.html`

Note: GitHub Pages may take 1-2 minutes to deploy after the push. The local file opens immediately.

---

## Important Execution Rules

### No Fabrication
- If data cannot be verified through web search, explicitly state: "Not publicly available"
- Use SPECULATIVE confidence badge for inferred information
- Never invent company metrics, financials, or initiatives not found in sources
- Use confidence levels consistently across all sections

### Source Transparency
- Every claim with factual content must have at least one source link
- Store all 25-35 search URLs in sources tab with publication dates
- Clickable links in HTML, not just text references
- Include source domain (e.g., "www.company.com/investors" vs generic "Company Website")

### Methodology Callouts
- Every analytical section includes ℹ️ icon with tooltip explaining framework used
- Tab 8 (Sources) provides detailed methodology explanations
- Confidence levels indicated for each major finding

### No Emojis in Report Content
- Only use ℹ️ for methodology callouts (structural, not content)
- No decorative emojis in analysis, tables, or text sections
- Professional tone maintained throughout

### Logo & Branding
- Artifact branding applied consistently across header
- Company logos embedded where available
- Professional color scheme matching McKinsey/consulting norms
- Clean, minimal design avoiding visual clutter

---

## Research Quality Standards

### Verification Hierarchy

**VERIFIED Sources (Preferred)**
- Company annual reports and investor disclosures
- Official press releases and company websites
- SEC filings (10-K, 8-K for US companies)
- Earnings call transcripts
- Patent databases (USPTO, WIPO)
- Regulatory filings (stock exchange disclosures)

**INFERRED Sources (Acceptable with Badge)**
- Industry analyst reports (Gartner, Forrester, McKinsey, BCG)
- News articles from reputable outlets (Reuters, Bloomberg, TechCrunch)
- Academic research papers
- Multiple secondary sources corroborating a finding
- Job postings indicating hiring/strategic focus

**SPECULATIVE Sources (Limited Use, Clearly Marked)**
- Social media statements by executives
- Rumors from industry forums
- Predictions extrapolated from trends
- Single-source claims without corroboration
- Analyst speculation on future strategy

### Data Recency Standards
- Company financials: Latest FY (within 12 months)
- News/developments: Last 6-12 months
- Industry trends: Last 2-3 years
- Market data: Latest available year
- AI hiring/talent: Last 3-6 months (most dynamic)

---

## Common Variations & Customization

### For Different Meeting Types

**C-Suite Executive (CEO/Board):**
- Emphasize strategic risk/opportunity
- Focus on Horizon 2 & 3 transformational use cases
- Highlight competitive differentiation
- Include market share and growth implications

**Technology Leader (CTO/VP Engineering):**
- Deep dive on technology stack and infrastructure
- Emphasis on technical feasibility and platform choices
- Detail on talent/capability building required
- MLOps maturity and scalability considerations

**Operations/Business Leader (COO/VP Operations):**
- Focus on cost reduction and efficiency gains
- Process automation and workflow improvements
- Implementation timeline and resource requirements
- Risk mitigation and business continuity

**Finance Leader (CFO/VP Finance):**
- ROI calculations with payback periods
- Cost-benefit analysis for each use case
- Capital requirements and investment phasing
- Financial risk and downside scenarios

### For Different Industries

**Technology/Software:**
- Emphasize data leverage and product enhancement
- Competitive AI adoption by peers
- Talent acquisition intensity
- Platform/ecosystem implications

**Healthcare/Pharma:**
- Regulatory compliance and governance requirements
- Clinical validation and evidence standards
- Patient data privacy (HIPAA) implications
- Talent shortage in domain expertise

**Financial Services:**
- Regulatory framework and compliance risk
- Fraud detection and risk management
- Customer experience and retention
- Cybersecurity and data security

**Manufacturing/Industrial:**
- Predictive maintenance and operational efficiency
- Supply chain optimization
- Quality control and yield improvement
- Workforce reskilling requirements

---

## Template Files & Assets

### report-template.html
Base HTML template with all CSS/JS embedded. No external dependencies.
Find using Glob: `**/intel-company/report-template.html`

### assets/
Logo files for Artifact branding. Must be in same directory as generated report.
Find using Glob: `**/intel-company/assets/`

### references/ai-maturity-model.md
Read this for detailed scoring rubrics when assessing AI maturity across 6 dimensions.

### references/use-case-library.md
Read this for industry-specific AI use case examples to inform the Top 8 recommendations.

---

## Execution Checklist

Before deploying dashboard, verify:

- [ ] All {{PLACEHOLDERS}} replaced with actual data
- [ ] 25-35 web searches executed and documented
- [ ] AI Maturity scores assigned with evidence for all 6 dimensions
- [ ] 8 AI use cases identified and prioritized
- [ ] Executive Summary completed with key findings
- [ ] All source links are clickable and functional
- [ ] Confidence badges (VERIFIED/INFERRED/SPECULATIVE) applied consistently
- [ ] Methodology callouts (ℹ️) present in every analytical section
- [ ] No emojis in report content (except methodology icons)
- [ ] Charts render correctly (Maturity Curve, Impact-Effort Matrix, Radar Chart)
- [ ] Logo assets embedded or copied to docs/
- [ ] GitHub repository initialized and configured for Pages deployment
- [ ] HTML file deployed to GitHub Pages
- [ ] Responsive design tested on mobile/tablet/desktop
- [ ] Tab navigation functional and all 8 tabs complete
- [ ] Company logo and CEO photo included in Executive Summary
- [ ] Meeting context addressed specifically in Engagement Strategy tab

---

## Quality Standards

### Completeness
- All 8 tabs contain substantive content (no placeholders or TODOs)
- Executive summary provides actionable insights, not just data summary
- Use cases are company-specific, not generic templates
- Sources span multiple research clusters (profile, competitive, AI, industry, recent)

### Credibility
- 80%+ of major claims supported by cited sources
- Speculative claims clearly marked and explained
- Analyst estimates attributed to named sources
- Data sources are reputable (SEC filings, company websites, tier-1 research firms)

### Usability
- Dashboard navigates smoothly across all 8 tabs
- Charts are readable at standard screen sizes
- Source links open in new tabs
- Methodology tooltips appear on hover
- Mobile display is readable (responsive design)

### Strategic Value
- Insights are non-obvious (not available in company annual reports alone)
- Recommendations are specific to company context
- Use cases reflect identified pain points
- Engagement strategy is actionable (talking points, anticipated objections)

---

## Support & Resources

For detailed analysis guidance, refer to:
- `references/ai-maturity-model.md` - Framework details and scoring rubrics for 6 AI maturity dimensions
- `references/use-case-library.md` - 50+ industry-specific use case examples for reference
