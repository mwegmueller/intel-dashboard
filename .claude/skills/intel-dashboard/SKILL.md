---
name: intel-dashboard
description: Use when the user asks for meeting preparation, meeting intelligence, or profile research on a person. Generate a comprehensive 8-tab HTML intelligence dashboard for meeting prep. Triggers on phrases like "meeting with", "prepare for meeting", "research [person]", "profile for [person]", "intel on [person]". Creates interactive HTML report with Executive Summary, Subject Profile, Network Map, Behavioral Analysis, Strategic Position, Engagement Playbook, Media Footprint, and AI Use Cases. Includes multi-language support (EN/DE/FR) with a language switcher button. Deploys to GitHub Pages. Use WebSearch for research, Write for HTML output, Bash for git deployment. Do NOT use browser/Chrome MCP tools.
---

# Sailor 2.0 - Meeting Intelligence Profile Generator

## CRITICAL: TEMPLATE AND ASSETS LOCATION

**BEFORE generating any report, you MUST:**

1. **Find the template** using Glob:
   ```
   Glob pattern: **/intel-dashboard/report-template.html
   ```

2. **Find the output directory** using Glob:
   ```
   Glob pattern: **/intel-dashboard/assets/
   ```
   The output directory is the PARENT of the assets folder (where `assets/` lives).

3. **Verify assets exist**: The `assets/` folder must contain:
   - `artifact-logo-horizontal.png` (header logo)
   - `artifact-logo-vertical.png` (alternate logo)

**The HTML template uses relative paths to assets (`assets/artifact-logo-horizontal.png`), so the generated report MUST be saved in the same directory as the `assets/` folder.**

## CRITICAL: SOURCE LINKS MUST BE CLICKABLE

**Every source in the Sources section MUST be a clickable link with an actual URL.**

During research, you MUST track the actual URLs of every source you use. When generating the report:

```html
<!-- CORRECT - with actual URL -->
<a href="https://www.linkedin.com/in/personname" target="_blank" class="source-item">
    <div class="source-icon">LI</div>
    <div class="source-info">
        <div class="source-name">LinkedIn Profile</div>
        <div class="source-meta">2024 | Professional</div>
    </div>
</a>

<!-- WRONG - no link -->
<div class="source-item">
    <div class="source-icon">LI</div>
    <div class="source-info">
        <div class="source-name">LinkedIn</div>
        <div class="source-meta">Executive profile</div>
    </div>
</div>
```

**Sources MUST use `<a href="URL" target="_blank">` NOT `<div>`**

## CRITICAL: METHODOLOGY CALLOUTS ON EVERY SECTION

**Every card/section MUST include a methodology callout (ℹ️ info icon) explaining how the data was gathered.**

The template includes methodology callouts that appear as hoverable info icons. These MUST be preserved and populated with appropriate explanations. Users need to understand the data provenance.

### Required Methodology Callouts (25 total):

| Section | Card/Element | Methodology Explanation |
|---------|--------------|------------------------|
| **Executive Summary** | Meeting Fit Score | "AI-ASSESSED: Score based on alignment between stated meeting purpose and subject's role, authority, and interests. Use as guidance, not absolute measure." |
| **Executive Summary** | How to Engage (DISC) | "AI-INFERRED: DISC assessment based on observable behavioral indicators from public content. Not a formal assessment." |
| **Executive Summary** | Key Facts | "Metrics extracted from LinkedIn profiles, company pages, and verified sources." |
| **Executive Summary** | Strategic Insights | "Insights synthesized from multiple sources. Patterns identified by analyzing recurring themes, stated priorities, and public positions." |
| **Executive Summary** | Conversation Openers | "Topics derived from recent activities, published interests, and meeting context alignment." |
| **Executive Summary** | Anticipated Topics | "Probability scores based on frequency of discussion in public content and meeting context relevance." |
| **Subject Profile** | Professional Timeline | "Extracted from LinkedIn public profile and company team pages. Dates verified against press releases where available." |
| **Subject Profile** | Recognition & Awards | "Collected from press releases, award announcements, and professional directory listings." |
| **Subject Profile** | Industry Expertise | "Tags derived from stated skills, published content topics, and project descriptions." |
| **Subject Profile** | Company Profile | "Data from Swiss business registry (Moneyhouse), company website, and Crunchbase/similar directories." |
| **Network Map** | Leadership Team | "From company registry records and team page. Roles verified via LinkedIn." |
| **Network Map** | Strategic Partners/Advisors | "Advisors identified from company pages, LinkedIn connections marked as advisors, and press mentions." |
| **Network Map** | Professional Affiliations | "Memberships and affiliations from LinkedIn, association directories, and conference speaker bios." |
| **Network Map** | Key Clients | "Clients identified from case studies, testimonials, and press releases. Sector inferred from industry focus." |
| **Behavioral Analysis** | Communication Style (Radar) | "⚠️ INFERRED: Radar scores based on linguistic analysis of published content. Higher scores = more frequent expression of that trait. Not a psychological assessment." |
| **Behavioral Analysis** | DISC Profile | "⚠️ AI-INFERRED: DISC assessment based on observable behavioral indicators from public content, communication style, and role characteristics. This is NOT a formal DISC assessment - use as meeting preparation guidance only." |
| **Behavioral Analysis** | Decision-Making Profile | "⚠️ INFERRED: Profile based on described approaches in interviews and case studies. Validate with direct interaction." |
| **Behavioral Analysis** | Psychological Indicators | "⚠️ AI-GENERATED: Patterns from content analysis. These are behavioral observations, not clinical assessments. Use as conversation guidance only." |
| **Behavioral Analysis** | Key Value Phrases | "Phrases extracted via NLP from articles, posts, and interviews. Frequency = how often they appear in public content." |
| **Strategic Position** | SWOT Analysis | "⚠️ AI-GENERATED: SWOT based on company positioning, market research, and competitive analysis. Recommendations are suggestions - validate with domain expertise." |
| **Strategic Position** | Competitive Positioning (Scatter) | "⚠️ AI-ESTIMATED: Positions based on market perception analysis. Axes are relative, not absolute measurements." |
| **Strategic Position** | Core Differentiators | "Self-stated differentiators from company website, pitch decks, and marketing materials." |
| **Engagement Playbook** | Strategy Banner | "Strategy generated based on behavioral analysis and stated priorities. Adapt based on your specific objectives and context." |
| **Engagement Playbook** | Conversation Starters | "Topics derived from recent activities, published interests, and areas of expertise." |
| **Engagement Playbook** | Topics to Avoid | "⚠️ AI-INFERRED: Based on stated values and potential sensitivities. Use judgment in actual conversation." |
| **Engagement Playbook** | Connection Points | "Potential common ground based on your provided context and their profile." |
| **Engagement Playbook** | Anticipated Topics | "Probability scores based on frequency of discussion in public content and meeting context relevance." |
| **Media Footprint** | Published Content | "Content discovered via web search and company blog archives." |
| **Media Footprint** | Speaking Appearances | "From conference speaker pages, event listings, and press coverage." |
| **Media Footprint** | Sentiment Analysis | "⚠️ AI-GENERATED: Sentiment from NLP classification of news coverage. Aggregate scores, not individual article analysis." |
| **Executive Summary** | Source Confidence | "Primary = official sources. Secondary = reputable news/industry sources. Inferred = cross-referenced patterns. Speculative = limited single-source data." |
| **Subject Profile** | Recent Activity | "Content from last 30-90 days sourced from LinkedIn posts, company news, and press releases. May not capture all activity." |
| **Behavioral Analysis** | Influence Levers | "⚠️ AI-INFERRED: Based on stated priorities, role characteristics, and communication patterns. Validate in actual conversation." |
| **Engagement Playbook** | Value Exchange Map | "⚠️ AI-GENERATED: Suggestions based on their stated needs and your context. Customize based on your actual capabilities." |
| **Engagement Playbook** | Contact Strategy | "Recommendations based on communication style analysis and professional norms. Adjust based on relationship status." |
| **Strategic Position** | Competitive Intelligence | "⚠️ SPECULATIVE: Based on market research and industry patterns. Actual competitive situation may differ." |

### Methodology Callout HTML Template:

```html
<span class="methodology-callout">
    <span class="methodology-icon">ℹ️</span> How generated
    <div class="methodology-tooltip">Your explanation of data source and methodology here.</div>
</span>
```

**DO NOT remove or skip methodology callouts from the template. They are essential for transparency.**

## OUTPUT FORMAT

**OUTPUT: Single-file HTML dashboard saved alongside the `assets/` folder**

This skill creates an **HTML file** (not Word, not DOCX, not Google Docs). The output is:
1. A `.html` file written using the `Write` tool
2. Saved in the same directory as `assets/` folder
3. Deployed to GitHub Pages via `Bash` git commands
4. Opened locally with `open` command

**NEVER create:**
- Word documents (.docx)
- Google Docs
- PDF files
- Any browser-based document

## ALLOWED TOOLS - USE ONLY THESE

1. `Glob` - find the template and output directory
2. `WebSearch` - research the person (run 10-20 searches)
3. `Read` - read the template file
4. `Write` - save the final HTML to the output directory
5. `Bash` - git commands and `open` command only

## FORBIDDEN TOOLS - NEVER USE

- Any tool starting with `mcp__`
- Browser tools
- Chrome extension tools
- Document creation tools
- Shortcuts or workflows

## Input Format

The user provides a free-form description that may include:
- Target person's name and role
- Their company
- Meeting purpose/occasion
- **OPTIONAL: Requestor's name** (for Personal Interests Matching feature)

**Example inputs:**
- "I'm meeting with Sarah Chen, CEO of TechCorp, to discuss a partnership"
- "Prepare me for a sales call with John Smith from Acme Inc"
- "Meeting prep: Maria Garcia, Head of AI at DataCo, for AI strategy workshop. I'm Jonas from SIX Group."
- **NEW FORMAT:** "Meeting with Edo Tersigni, Galderma, AI strategy. My name is Michael Wegmüller." (enables Personal Interests Matching)

### Input Parsing Rules

1. **If requestor name IS provided**: Enable Personal Interests Matching section
2. **If requestor name is NOT provided**: Skip Personal Interests Matching section entirely

## Execution Steps

### Step 1: Locate Template and Output Directory

**CRITICAL - DO THIS FIRST:**

```
1. Use Glob to find: **/intel-dashboard/report-template.html
2. Use Glob to find: **/intel-dashboard/assets/
3. The OUTPUT_DIR is the parent of assets/ (e.g., /path/to/intel-dashboard/)
4. Read the template file
```

If template or assets are not found, inform the user and ask them to provide the correct location.

### Step 2: Parse the Request

Extract:
- `targetName`: The person to research
- `targetRole`: Their job title
- `targetCompany`: Their organization
- `meetingPurpose`: What the meeting is about
- `requestorName`: Name of the person requesting (OPTIONAL - enables Personal Interests Matching)
- `requestorContext`: Additional info about the person requesting (if provided)

If target name or company is missing, ask the user.

### Step 3: Research (Run 20+ Web Searches) - TRACK ALL URLs

Execute these searches IN PARALLEL where possible. **IMPORTANT: Save the actual URL of every source you find for the Sources section.**

**Person Profile (6 searches):**
1. `"{targetName}" "{targetCompany}"` - basic profile overview
2. `"{targetName}" LinkedIn profile` - professional background
3. `"{targetName}" biography` - detailed bio information
4. `"{targetName}" career history previous roles` - career trajectory
5. `"{targetName}" education university degree` - educational background
6. `"{targetName}" location based` - geographic information

**Achievements & Recognition (3 searches):**
7. `"{targetName}" award winner recognition` - awards received
8. `"{targetName}" Forbes Fortune business leader` - business media recognition
9. `"{targetCompany}" award winning` - company accolades

**Network & Relationships (4 searches):**
10. `"{targetCompany}" founders leadership team executives` - leadership network
11. `"{targetCompany}" board of directors advisory` - board connections
12. `"{targetCompany}" investors funding` - investor relationships
13. `"{targetCompany}" partners partnerships` - strategic partners

**Published Content & Thought Leadership (4 searches):**
14. `"{targetName}" article blog post medium` - written content
15. `"{targetName}" interview podcast` - media interviews
16. `"{targetName}" speaking keynote conference` - speaking engagements
17. `"{targetName}" quotes said stated` - notable quotes and positions

**Company Intelligence (5 searches):**
18. `"{targetCompany}" about company founded history` - company background
19. `"{targetCompany}" products services offerings` - what they sell
20. `"{targetCompany}" clients customers case study` - client relationships
21. `"{targetCompany}" competitors market position` - competitive landscape
22. `"{targetCompany}" news recent announcement` - recent developments

**Social Media & Online Presence (2 searches):**
23. `"{targetName}" Twitter X posts` - social media presence
24. `"{targetName}" GitHub open source` - technical contributions (if relevant)

**Profile Picture (1 search):**
25. `"{targetName}" "{targetCompany}" photo headshot` - find a professional photo URL

**Personal Interests (2 searches):**
26. `"{targetName}" hobbies interests outside work personal` - personal interests
27. `"{targetName}" marathon charity volunteer sports` - activities outside work

**AI Use Cases Context (2 searches):**
28. `"{targetCompany}" AI use cases digital transformation challenges` - company AI context
29. `"{targetRole}" AI applications automation opportunities` - role-specific AI applications

### Step 3b: Requestor Research (ONLY if requestor name provided)

**CRITICAL: This research is COMPLETELY SEPARATE from target research. NEVER mix data.**

**Only run these searches AFTER completing all target research:**
30. `"{requestorName}" hobbies interests outside work personal` - requestor personal interests
31. `"{requestorName}" volunteer charity sports marathon` - requestor activities

**Track for each source:**
- Actual URL (for clickable links)
- Source name
- Type (LinkedIn, News, Company Page, etc.)
- Year accessed
- Confidence level: VERIFIED, INFERRED, or SPECULATIVE

### Step 4: Synthesize Intelligence

Organize findings into 8 sections (+ optional Personal Interests):

**1. Executive Summary** (McKINSEY SENIOR PARTNER LAYOUT)
The Executive Summary is the single most important tab. It must read like a McKinsey senior partner's pre-meeting brief: crisp, actionable, zero fluff. A partner has 90 seconds before walking into the room. Every word must earn its place.

Layout (top to bottom):
- **BLUF** - 2-3 sentences MAXIMUM. State: who they are, why this meeting matters, one key leverage point. Bold the most critical fact. No background filler.
- **Three-card row**: Meeting Fit Score (ring visual, 1-10) | How to Engage (DISC primary type + one-liner communication tip) | Key Facts (2 metrics only - years experience + most relevant metric)
- **Two-column row**: Strategic Insights (3 compact insights, each 1-2 sentences - the "so what" for your meeting) | Conversation Openers (4 numbered questions ready to use verbatim)
- **Anticipated Topics table** (4 rows: topic, probability badge, "Your Angle" column with prep notes)
- **Source Confidence** - compact inline bar at bottom, NOT a pie chart. This is metadata, not the main event.

**CRITICAL RULES for Executive Summary:**
- NO verbose paragraphs in BLUF. If your BLUF is more than 3 sentences, cut it.
- Strategic Insights are NOT "Deep Analysis" - they are the 3 things the partner needs to know to win this meeting. Each insight has a bold title and 1-2 sentence explanation.
- Conversation Openers must be actual questions you can ask word-for-word. Not topics. Questions.
- "Your Angle" in Anticipated Topics tells the partner exactly how to position on that topic.

**2. Subject Profile**
- Professional timeline
- **NEW: Recent Activity** (last 30-90 days - LinkedIn posts, news, announcements)
- Recognition & awards
- Industry expertise
- Company profile metrics

**3. Network Map**
- Co-founders/partners
- Advisory relationships
- Professional affiliations
- Key clients
- **NEW: Relationship Proximity** (if requestor context provided - shared connections, intro paths)

**4. Behavioral Analysis**
- Communication style indicators (8-dimension radar)
- **DISC Profile Assessment** (REQUIRED - see DISC section below)
- Decision-making profile
- **NEW: Influence Levers** (what motivates their decisions - speed, quality, cost, relationships, risk tolerance)
- Psychological indicators
- Key value phrases

**5. Strategic Position**
- **Engagement-focused SWOT** (framed around meeting objectives, not just company analysis)
- Competitive positioning
- Core differentiators
- **NEW: Competitive Intelligence** (who else might they be evaluating/talking to)

**6. Engagement Playbook**
- Meeting-specific strategy
- **NEW: Value Exchange Map** (what YOU can offer THEM based on their needs)
- **NEW: Optimal Contact Strategy** (channel, timing, formality level)
- Conversation starters
- Topics to approach carefully
- Connection points (if requestor context provided)
- Anticipated discussion topics

**7. Media Footprint**
- Published content
- Speaking engagements
- Media sentiment (with explicit methodology caveat)

**8. AI Use Cases (NEW TAB)**
- 6-8 AI use cases tailored to the person's role, industry, and challenges
- Visual card grid layout (like a presentation slide)
- Each card has: title, short description, mouseover popup with reasoning
- Based on: their industry, role responsibilities, company challenges, stated interests

**9. Personal Interests Matching (NEW - only if requestor name provided)**
- **CRITICAL: Sequential research - NEVER mix target and requestor data**
- Personal interests of the target person
- Personal interests of the requestor (separate research)
- Interest overlap analysis (computed AFTER both are researched separately)
- Connection opportunities based on shared interests

### Step 4b: Prepare AI Use Cases Impact/Feasibility Map

For the 8 AI use cases, rate each on two axes (1-100 scale):
- **Impact** (Y-axis): How transformative would this use case be for the company?
- **Feasibility** (X-axis): How easy is it to implement given current infrastructure and skills?

Position each use case on the scatter map. Use the `uc-dot` CSS class with numbered circles (1-8).

**UC Scatter Dot Template:**
```html
<div class="uc-dot uc1" style="left: 80%; bottom: 90%;">
    <span>1</span>
    <div class="scatter-tooltip">
        <strong>#1: Use Case Title</strong><br>
        Impact: Very High | Feasibility: High<br>
        <em>Rationale: This use case targets the company's core pain point of X, and existing data infrastructure makes implementation straightforward.</em>
    </div>
</div>
```

**UC Legend Item Template:**
```html
<div class="uc-legend-item">
    <div class="uc-legend-dot" style="background: #8b5cf6;"></div>
    <span>1. Use Case Title</span>
</div>
```

**Color mapping:** uc1=#8b5cf6, uc2=#3b82f6, uc3=#10b981, uc4=#f59e0b, uc5=#ef4444, uc6=#ec4899, uc7=#06b6d4, uc8=#84cc16

### Step 5: Generate Dashboard & Deploy

**USE THESE SPECIFIC TOOLS - NO BROWSER TOOLS:**

1. **Generate unique report token** (use Bash tool):
```bash
date +%s | shasum | head -c 8
```
Store this 8-character token.

2. **Read the template** (use Read tool):
Read the template file found in Step 1.

3. **Create the HTML content:**
- Replace all `{{PLACEHOLDER}}` values with researched data
- **PRESERVE all methodology callouts** - update their tooltip text with actual methodology
- **Use actual URLs** for all source items (as `<a href>` tags)

4. **Create filename:**
Format: `{firstname}-{lastname}-{token}.html` (lowercase, hyphens)
Example: `marcel-salathe-8cea1670.html`

5. **Save the report** (use Write tool - NOT Bash):
Write to: `{OUTPUT_DIR}/{filename}.html`
**IMPORTANT**: Must be in same directory as `assets/` folder for logos to display.

6. **Deploy to GitHub Pages** (use Bash tool):

**CRITICAL: The git repo may have diverged from remote. Follow this exact sequence to avoid push failures:**

```bash
# Step 1: Pull remote changes first (rebase to keep history clean)
cd {OUTPUT_DIR} && git pull --rebase origin gh-pages || git pull origin gh-pages --no-rebase

# Step 2: Stage and commit the new report
git add {filename}.html && git commit -m "Add profile: {targetName}"

# Step 3: Push to remote
git push origin gh-pages
```

**If push fails** (e.g., authentication, diverged branches), try these fallbacks in order:
1. `git pull --rebase origin gh-pages && git push origin gh-pages` (rebase and retry)
2. If auth fails, inform the user: "Push failed - you may need to run `git push origin gh-pages` manually or set up a credential helper."

**Notes for claude cowork / headless environments:**
- Git credential helper must be pre-configured (e.g., `osxkeychain`, `store`, or SSH keys)
- If running in a cowork session without interactive auth, the push may fail. In that case, save the file locally and inform the user to push manually.
- Never use `--force` push. If branches have truly diverged, merge and resolve.

7. **Open locally** (use Bash tool):
```bash
open {OUTPUT_DIR}/{filename}.html
```

8. **Return the shareable URL to the user:**
`https://mwegmueller.github.io/intel-dashboard/{filename}.html`
(Note: URL will only work after successful push and GitHub Pages build, which takes ~1-2 minutes)

### Step 5b: Generate Translations (DE + FR) — REQUIRED

**CRITICAL: This step is MANDATORY and happens AFTER the English report is written and deployed. Do NOT skip this step. Do NOT leave `{{TRANSLATIONS_JSON}}` as empty `{}` — the language switcher will not work without actual translation data.**

The report template includes a `{{TRANSLATIONS_JSON}}` placeholder that must be populated with a complete JSON object containing German and French translations of ALL text content.

**Process:**
1. After writing the English HTML report, identify ALL `data-i18n` and `data-i18n-html` keys used in the report
2. Generate complete German (de) and French (fr) translations for EVERY key — typically 60-70 keys
3. Update the HTML file by replacing `try { translations = {{TRANSLATIONS_JSON}}; }` with `try { translations = {ACTUAL_JSON}; }` — the JSON must be a valid JavaScript object literal, NOT a string

**Translation scope - translate EVERYTHING including:**
- Tab names and mobile tab names
- Section headings (BLUF label, Meeting Fit, How to Engage, etc.)
- All content: BLUF text, strategic insights, conversation openers, anticipated topics
- SWOT items, engagement strategy, playbook content
- AI use case titles, descriptions, and reasoning
- Table headers (Topic, Probability, Your Angle, etc.)
- Button labels (Share, PDF)
- Axis labels on charts
- Methodology tooltip text

**Do NOT translate:**
- Proper nouns (person names, company names)
- Scores and numbers
- URLs
- CSS class names or HTML structure
- DISC type letters (D, I, S, C)

**Translation JSON format:**
```json
{
    "de": {
        "tab_executive_summary": "Zusammenfassung",
        "tab_subject_profile": "Personenprofil",
        "tab_network_map": "Netzwerkkarte",
        "tab_behavioral_analysis": "Verhaltensanalyse",
        "tab_strategic_position": "Strategische Position",
        "tab_engagement_playbook": "Engagement-Leitfaden",
        "tab_media_footprint": "Medienprasenz",
        "tab_ai_use_cases": "KI-Anwendungsfalle",
        "bluf_label": "KERNAUSSAGE",
        "bluf_content": "[Full German translation of BLUF]",
        "meeting_fit": "Meeting-Eignung",
        "strategic_insights": "Strategische Erkenntnisse",
        "conversation_openers": "Gesprachseroffnungen",
        "strategic_insights_content": "[Full HTML of translated insights]",
        "exec_openers_content": "[Full HTML of translated openers]",
        "swot_strengths": "Starken",
        "swot_weaknesses": "Schwachstellen",
        "swot_opportunities": "Chancen",
        "swot_threats": "Wettbewerbsrisiken",
        "swot_strengths_list": "[Full HTML of translated SWOT strengths]",
        "engagement_strategy": "[Full HTML of translated strategy]",
        "ai_use_cases_title": "KI-Anwendungsfalle - Auswirkung vs. Machbarkeit",
        "axis_impact": "Geschaftliche Auswirkung",
        "axis_feasibility": "Umsetzbarkeit",
        "btn_share": "Teilen",
        "btn_download": "PDF"
    },
    "fr": {
        "tab_executive_summary": "Resume Executif",
        "tab_subject_profile": "Profil du Sujet",
        "bluf_label": "L'ESSENTIEL EN BREF",
        "bluf_content": "[Full French translation of BLUF]",
        "meeting_fit": "Adequation",
        "strategic_insights": "Perspectives Strategiques",
        "ai_use_cases_title": "Cas d'Usage IA - Impact vs. Faisabilite",
        "axis_impact": "Impact Commercial",
        "axis_feasibility": "Faisabilite de Mise en Oeuvre",
        "btn_share": "Partager",
        "btn_download": "PDF"
    }
}
```

**Implementation:**
1. Read the generated HTML file
2. Replace `{{TRANSLATIONS_JSON}}` with the complete JSON object (NOT a string - it must be valid JS)
3. Write the updated HTML file back
4. Re-deploy to GitHub Pages (git add, commit, push)

**Language switcher behavior:**
- Green globe button in the FAB group (bottom-right)
- Cycles: EN → DE → FR → EN
- Shows current language code (EN/DE/FR) on the button
- Toast notification shows language name on switch

## Placeholder Reference

### Header
- `{{TARGET_NAME}}` - Person's full name (NO emojis)
- `{{TARGET_ROLE}}` - Job title
- `{{TARGET_COMPANY}}` - Company name
- `{{PROFILE_PHOTO_URL}}` - URL to person's professional headshot (from LinkedIn, company site, or news)
- `{{LOCATION}}` - Geographic location (NO emojis, just text)
- `{{EDUCATION}}` - Educational background
- `{{WEBSITE}}` - Company/personal website
- `{{ADDITIONAL_INFO}}` - Other notable info
- `{{SOURCE_COUNT}}` - Number of sources found

### Executive Summary (McKinsey Layout)
- `{{BLUF_CONTENT}}` - 2-3 sentences MAX. Bold the key fact. No filler. (NO emojis)
- `{{MEETING_FIT_SCORE}}` - 1-10 score (integer)
- `{{FIT_SCORE_CLASS}}` - CSS class: "high" (8-10), "medium" (5-7), "low" (1-4)
- `{{MEETING_FIT_RATIONALE}}` - One sentence why this score
- `{{DISC_PRIMARY_TYPE}}` - e.g., "D" or "I" or "S" or "C"
- `{{DISC_PRIMARY_CLASS}}` - CSS class: "d", "i", "s", or "c" (lowercase)
- `{{DISC_PRIMARY_LABEL}}` - e.g., "Dominant - Results-Driven"
- `{{DISC_COMMUNICATION_TIPS}}` - 1-2 sentence actionable tip for engaging this DISC type
- `{{CONFIDENCE_LEVEL}}` - HIGH CONFIDENCE / MEDIUM CONFIDENCE / LIMITED DATA
- `{{YEARS_EXPERIENCE}}` - e.g., "17+"
- `{{KEY_METRIC}}` - e.g., "+85" (single most relevant metric for this person)
- `{{KEY_METRIC_LABEL}}` - e.g., "NPS Score"
- `{{STRATEGIC_INSIGHTS}}` - 3 exec-insight blocks (see template below)
- `{{EXEC_CONVERSATION_OPENERS}}` - 4 exec-opener blocks (see template below)
- `{{EXEC_ANTICIPATED_TOPICS}}` - 4 table rows: topic, probability badge, "Your Angle" prep note
- `{{PRIMARY_PCT}}`, `{{SECONDARY_PCT}}`, `{{INFERRED_PCT}}`, `{{SPECULATIVE_PCT}}` - Source percentages (e.g., "35%")
- `{{SOURCE_COUNT}}` - Total number of sources

**Strategic Insight block:**
```html
<div class="exec-insight">
    <div class="exec-insight-title">Insight Title</div>
    <div class="exec-insight-text">One to two sentence actionable insight.</div>
</div>
```

**Conversation Opener block:**
```html
<div class="exec-opener">
    <div class="exec-opener-num">1</div>
    <div>"Actual question you can ask verbatim?"</div>
</div>
```

**Anticipated Topics row:**
```html
<tr>
    <td>Topic Name</td>
    <td><span class="probability-badge prob-very-high">Very High</span></td>
    <td>Your specific angle/positioning for this topic</td>
</tr>
```

### Subject Profile
- `{{PROFESSIONAL_TIMELINE}}` - Timeline item HTML
- `{{RECENT_ACTIVITY}}` - Recent 30-90 days activity (LinkedIn posts, news, announcements) - media item HTML
- `{{RECOGNITION_AWARDS}}` - Media item HTML
- `{{INDUSTRY_TAGS}}` - Tag span HTML
- `{{COMPANY_FOUNDED}}`, `{{COMPANY_FOUNDERS}}`, `{{COMPANY_SIZE}}`, `{{COMPANY_METRIC}}`, `{{COMPANY_METRIC_LABEL}}`, `{{COMPANY_EXPERIENCE}}`, `{{COMPANY_LOCATION}}`

### Network Map
- `{{COFOUNDERS_LIST}}` - Person card HTML
- `{{ADVISORS_LIST}}` - Person card HTML
- `{{AFFILIATIONS_LIST}}` - Conversation card HTML
- `{{CLIENTS_TAGS}}` - Tag span HTML

### Behavioral Analysis
- `{{RADAR_POINTS}}` - SVG polygon points for 8-dimension radar chart (format: "x1,y1 x2,y2 x3,y3 x4,y4 x5,y5 x6,y6 x7,y7 x8,y8")
- `{{DISC_D_SCORE}}` - Dominance score (0-100) - REQUIRED
- `{{DISC_I_SCORE}}` - Influence score (0-100) - REQUIRED
- `{{DISC_S_SCORE}}` - Steadiness score (0-100) - REQUIRED
- `{{DISC_C_SCORE}}` - Conscientiousness score (0-100) - REQUIRED
- `{{DISC_PRIMARY_TYPE}}` - Primary DISC type (D, I, S, or C)
- `{{DISC_SECONDARY_TYPE}}` - Secondary DISC type (if applicable)
- `{{DISC_DESCRIPTION}}` - Description of the person's DISC profile
- `{{DISC_COMMUNICATION_TIPS}}` - How to communicate with this DISC type
- `{{INFLUENCE_LEVERS}}` - Insight boxes for what motivates their decisions (speed/quality/cost/relationships/risk)
- `{{DECISION_PROFILE}}` - Table row HTML
- `{{PSYCHOLOGICAL_INDICATORS}}` - Insight box HTML
- `{{KEY_PHRASES}}` - Table row HTML

### Strategic Position
- `{{SWOT_STRENGTHS}}`, `{{SWOT_WEAKNESSES}}`, `{{SWOT_OPPORTUNITIES}}`, `{{SWOT_THREATS}}` - List item HTML
- `{{SCATTER_DOTS}}` - Positioned div HTML
- `{{COMPETITOR_LEGEND}}` - Legend item HTML
- `{{DIFFERENTIATORS}}` - Differentiator box HTML

### Engagement Playbook
- `{{MEETING_PURPOSE}}` - The occasion
- `{{ENGAGEMENT_STRATEGY}}` - Strategy paragraph
- `{{VALUE_EXCHANGE_MAP}}` - What YOU can offer THEM (insight boxes based on their stated needs)
- `{{CONTACT_STRATEGY}}` - Optimal outreach approach (channel, timing, formality) - insight box
- `{{CONVERSATION_STARTERS}}` - Conversation card HTML
- `{{TOPICS_TO_AVOID}}` - Warning card HTML
- `{{CONNECTION_POINTS}}` - Insight box HTML
- `{{ANTICIPATED_TOPICS}}` - Table row HTML

### Media Footprint
- `{{PUBLISHED_CONTENT}}` - Media item HTML
- `{{SPEAKING_APPEARANCES}}` - Media item HTML
- `{{SENTIMENT_BARS}}` - Bar group HTML

### AI Use Cases (Tab 8)
- `{{UC_SCATTER_DOTS}}` - 8 positioned uc-dot divs for the Impact/Feasibility scatter map
- `{{UC_SCATTER_LEGEND}}` - Legend mapping dot numbers/colors to use case names
- `{{AI_USE_CASES}}` - 6-8 use case cards HTML (see template below)

### Translations
- `{{TRANSLATIONS_JSON}}` - Complete JSON object with DE and FR translations (see Step 5b)

### Personal Interests Matching (NEW - only if requestor name provided)
- `{{TARGET_PERSONAL_INTERESTS}}` - Target's hobbies, interests, activities - tag list
- `{{REQUESTOR_NAME}}` - Name of the person requesting the report
- `{{REQUESTOR_PERSONAL_INTERESTS}}` - Requestor's hobbies, interests, activities - tag list
- `{{INTERESTS_OVERLAP}}` - Shared interests analysis - insight boxes
- `{{CONNECTION_OPPORTUNITIES}}` - How to leverage shared interests in conversation

### Sources Section
- `{{SOURCES_LIST}}` - Source item HTML - **MUST use `<a href="URL">` with actual URLs**

### Footer
- `{{GENERATION_DATE}}` - Current date
- `{{REQUESTOR_NAME}}` - Who requested
- `{{ORIGINAL_PROMPT}}` - The original user request/prompt
- `{{REPORT_TOKEN}}` - Unique 8-character token for this report

## HTML Component Templates

**Timeline Item:**
```html
<div class="timeline-item">
    <div class="timeline-period">2020 - Present</div>
    <div class="timeline-content">Role, Company</div>
</div>
```

**Person Card:**
```html
<div class="person-card">
    <div class="person-avatar">AB</div>
    <div class="person-info">
        <h4>Name</h4>
        <p>Role | Background</p>
    </div>
</div>
```

**Insight Box:** (colors: yellow, red, green, blue, orange)
```html
<div class="insight-box yellow">
    <div class="insight-title">Title:</div>
    <p>Description</p>
</div>
```

**Conversation Card:**
```html
<div class="conversation-card">
    <h4>Topic</h4>
    <p>"Question?"</p>
</div>
```

**Warning Card:**
```html
<div class="conversation-card warning">
    <h4>Topic</h4>
    <p>Why to be careful</p>
</div>
```

**Tag:**
```html
<span class="tag">Label</span>
```

**Bar Chart Group (with tooltip):**
```html
<div class="bar-group">
    <div class="bar-tooltip">2024: 60% positive, 30% neutral, 10% critical</div>
    <div class="bar" style="height: 150px;">
        <div class="bar-segment positive" style="height: 60%;"></div>
        <div class="bar-segment neutral" style="height: 30%;"></div>
        <div class="bar-segment critical" style="height: 10%;"></div>
    </div>
    <span class="bar-label">2024</span>
</div>
```

**Source Item (MUST include actual URL):**
```html
<a href="https://actual-source-url.com/page" target="_blank" class="source-item">
    <div class="source-icon">SC</div>
    <div class="source-info">
        <div class="source-name">Source Name</div>
        <div class="source-meta">2024 | Type</div>
    </div>
</a>
```

**Scatter Dot (with rationale tooltip):**
```html
<div class="scatter-dot subject" style="left: 75%; bottom: 80%;">
    <div class="scatter-tooltip">
        <strong>Company Name</strong><br>
        Agility: High | Expertise: High<br>
        <em>Leading market position driven by 20+ years domain expertise and rapid AI/ML adoption across all service lines.</em>
    </div>
</div>
```
**IMPORTANT**: Every scatter dot tooltip MUST include a rationale explaining WHY the company is positioned at that particular point on the axes. Don't just state "High/Low" — explain the reasoning.

**Interactive SWOT Item (with recommendation):**
```html
<li>
    <div class="interactive-item">
        Strength description
        <div class="item-recommendation">
            <div class="item-recommendation-label">Recommendation</div>
            How to leverage this strength in the meeting
        </div>
    </div>
</li>
```

**Methodology Callout (MUST be on every section):**
```html
<span class="methodology-callout">
    <span class="methodology-icon">ℹ️</span> How generated
    <div class="methodology-tooltip">Explanation of how this data was gathered and its confidence level.</div>
</span>
```

**Meeting Fit Score (built into Executive Summary three-card row):**
The Meeting Fit Score is now integrated directly into the Executive Summary as a ring visual. Use `FIT_SCORE_CLASS`: "high" (8-10), "medium" (5-7), "low" (1-4). The score integer goes in `{{MEETING_FIT_SCORE}}` and the rationale (1 sentence) in `{{MEETING_FIT_RATIONALE}}`.

**Recent Activity Card (NEW - add to Subject Profile):**
```html
<div class="card">
    <div class="card-header">
        <h3 class="card-title">Recent Activity (Last 90 Days)
            <span class="methodology-callout">
                <span class="methodology-icon">ℹ️</span> How sourced
                <div class="methodology-tooltip">Content from last 30-90 days sourced from LinkedIn posts, company news, and press releases.</div>
            </span>
        </h3>
        <span class="badge badge-verified">RECENT</span>
    </div>
    {{RECENT_ACTIVITY}}
</div>
```

**Value Exchange Map (NEW - add to Engagement Playbook):**
```html
<div class="card">
    <div class="card-header">
        <h3 class="card-title">What You Can Offer Them
            <span class="methodology-callout">
                <span class="methodology-icon">ℹ️</span> How generated
                <div class="methodology-tooltip">⚠️ AI-GENERATED: Suggestions based on their stated needs and your context.</div>
            </span>
        </h3>
        <span class="badge" style="background: var(--green-verified); color: white;">VALUE EXCHANGE</span>
    </div>
    {{VALUE_EXCHANGE_MAP}}
</div>
```

**Contact Strategy Card (NEW - add to Engagement Playbook):**
```html
<div class="card">
    <div class="card-header">
        <h3 class="card-title">Optimal Contact Strategy
            <span class="methodology-callout">
                <span class="methodology-icon">ℹ️</span> How determined
                <div class="methodology-tooltip">Recommendations based on communication style analysis and professional norms.</div>
            </span>
        </h3>
    </div>
    <table class="profile-table">
        <tr><td>Preferred Channel</td><td>{{CONTACT_CHANNEL}}</td></tr>
        <tr><td>Optimal Timing</td><td>{{CONTACT_TIMING}}</td></tr>
        <tr><td>Formality Level</td><td>{{CONTACT_FORMALITY}}</td></tr>
        <tr><td>First Touchpoint</td><td>{{CONTACT_FIRST_TOUCH}}</td></tr>
    </table>
</div>
```

**Influence Levers (NEW - add to Behavioral Analysis):**
```html
<div class="card">
    <div class="card-header">
        <h3 class="card-title">Influence Levers
            <span class="methodology-callout">
                <span class="methodology-icon">ℹ️</span> How inferred
                <div class="methodology-tooltip">⚠️ AI-INFERRED: Based on stated priorities, role characteristics, and communication patterns.</div>
            </span>
        </h3>
        <span class="badge badge-inferred">INFERRED</span>
    </div>
    {{INFLUENCE_LEVERS}}
</div>
```

**Profile Photo in Header (NEW):**
```html
<div class="header">
    <div class="header-brand">...</div>
    <div class="header-main" style="display: flex; align-items: center; gap: 24px;">
        <img src="{{PROFILE_PHOTO_URL}}" alt="{{TARGET_NAME}}" class="profile-photo"
             onerror="this.style.display='none'; document.querySelector('.profile-initials').style.display='flex';">
        <div class="profile-initials" style="display: none;">{{INITIALS}}</div>
        <div>
            <h1>{{TARGET_NAME}}</h1>
            <div class="header-subtitle">{{TARGET_ROLE}} | {{TARGET_COMPANY}}</div>
            <div class="header-meta">...</div>
        </div>
    </div>
</div>
```

**Profile Photo CSS:**
```css
.profile-photo { width: 100px; height: 100px; border-radius: 50%; object-fit: cover; border: 3px solid rgba(255,255,255,0.3); }
.profile-initials { width: 100px; height: 100px; border-radius: 50%; background: linear-gradient(135deg, #60a5fa, #3b82f6); display: flex; align-items: center; justify-content: center; font-size: 2.5rem; font-weight: 700; color: white; border: 3px solid rgba(255,255,255,0.3); }
```

**AI Use Cases Tab (NEW - Tab 8):**
```html
<div id="ai-use-cases" class="tab-content">
    <div class="card">
        <div class="card-header">
            <h3 class="card-title">Recommended AI Use Cases
                <span class="methodology-callout">
                    <span class="methodology-icon">ℹ️</span> How generated
                    <div class="methodology-tooltip">AI-GENERATED: Use cases selected based on person's role, industry, company challenges, and stated interests. Reasoning available on hover.</div>
                </span>
            </h3>
            <span class="badge" style="background: linear-gradient(135deg, #8b5cf6, #a78bfa); color: white;">AI OPPORTUNITIES</span>
        </div>
        <p style="font-size: 0.9rem; color: var(--slate-gray); margin-bottom: 20px;">
            Based on {{TARGET_NAME}}'s role as {{TARGET_ROLE}} at {{TARGET_COMPANY}}, these AI applications could be highly relevant:
        </p>
        <div class="use-cases-grid">
            {{AI_USE_CASES}}
        </div>
    </div>
</div>
```

**AI Use Case Card Template:**
```html
<div class="use-case-card">
    <div class="use-case-icon">📄</div> <!-- MUST be an emoji, NOT text like "DOC" -->
    <h4 class="use-case-title">{{USE_CASE_TITLE}}</h4>
    <p class="use-case-description">{{USE_CASE_DESCRIPTION}}</p>
    <div class="use-case-reasoning">
        <div class="reasoning-label">Why This Use Case?</div>
        <p>{{USE_CASE_REASONING}}</p>
    </div>
</div>
```
**Recommended Use Case Emojis:** 📄 (documents), 🤖 (chatbot/AI), ⚖️ (compliance/legal), 💡 (productivity/ideas), 📊 (analytics/data), 💰 (finance/wealth), 🛡️ (security/fraud), 🔍 (search/quality), 🏭 (operations), 🎯 (targeting/optimization), 🔄 (automation), 📱 (mobile/digital)

**AI Use Cases CSS:**
```css
.use-cases-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; }
.use-case-card { background: linear-gradient(135deg, #f8f9fa, #ffffff); border: 1px solid #e5e7eb; border-radius: 12px; padding: 24px; position: relative; transition: all 0.3s; cursor: pointer; }
.use-case-card:hover { transform: translateY(-4px); box-shadow: 0 12px 40px rgba(0,0,0,0.12); border-color: #8b5cf6; }
.use-case-icon { font-size: 2rem; margin-bottom: 12px; }
.use-case-title { font-size: 1.1rem; font-weight: 600; margin-bottom: 8px; color: var(--charcoal); }
.use-case-description { font-size: 0.9rem; color: var(--slate-gray); line-height: 1.6; }
.use-case-reasoning { display: none; position: absolute; top: 100%; left: 0; right: 0; margin-top: 8px; background: var(--navy); color: white; padding: 16px; border-radius: 8px; font-size: 0.85rem; z-index: 100; box-shadow: 0 8px 30px rgba(0,0,0,0.2); }
.use-case-card:hover .use-case-reasoning { display: block; }
.reasoning-label { font-weight: 600; color: #60a5fa; margin-bottom: 8px; font-size: 0.75rem; text-transform: uppercase; }
```

**Personal Interests Matching Section (NEW - add to Engagement Playbook, ONLY if requestor name provided):**
```html
<div class="card">
    <div class="card-header">
        <h3 class="card-title">Personal Interests Matching
            <span class="methodology-callout">
                <span class="methodology-icon">ℹ️</span> How researched
                <div class="methodology-tooltip">⚠️ INFERRED: Personal interests discovered from public profiles, interviews, and social media. Research conducted SEPARATELY for each person to avoid data mixing.</div>
            </span>
        </h3>
        <span class="badge" style="background: linear-gradient(135deg, #ec4899, #f472b6); color: white;">PERSONAL CONNECTION</span>
    </div>

    <div class="grid-2" style="margin-bottom: 20px;">
        <div>
            <h4 style="font-weight: 600; margin-bottom: 12px;">{{TARGET_NAME}}'s Interests</h4>
            <div class="tags">{{TARGET_PERSONAL_INTERESTS}}</div>
        </div>
        <div>
            <h4 style="font-weight: 600; margin-bottom: 12px;">{{REQUESTOR_NAME}}'s Interests</h4>
            <div class="tags">{{REQUESTOR_PERSONAL_INTERESTS}}</div>
        </div>
    </div>

    <div style="background: linear-gradient(135deg, #fdf2f8, #fce7f3); padding: 20px; border-radius: 8px; border: 1px solid #fbcfe8;">
        <h4 style="font-weight: 600; margin-bottom: 12px; color: #be185d;">Shared Interests & Connection Points</h4>
        {{INTERESTS_OVERLAP}}
    </div>

    <div class="insight-box" style="border-color: #ec4899; margin-top: 16px;">
        <div class="insight-title" style="color: #ec4899;">Conversation Opportunities:</div>
        <p>{{CONNECTION_OPPORTUNITIES}}</p>
    </div>
</div>
```

## DISC Profile Assessment Framework

The DISC model (developed by William Moulton Marston) describes four behavioral styles. Score each dimension 0-100 based on observable indicators from research.

### The Four DISC Dimensions

**D - Dominance (Results-oriented, Direct)**
- **High D indicators**: Direct communication, focus on results/achievements, competitive language, leadership roles, talks about goals/outcomes, impatient with details, makes quick decisions
- **Low D indicators**: Collaborative approach, consensus-seeking, avoids confrontation, supportive language

**I - Influence (People-oriented, Enthusiastic)**
- **High I indicators**: Enthusiastic/optimistic tone, networking focus, charismatic presence, motivational language, storytelling, social media active, relationship-focused
- **Low I indicators**: Reserved communication, data-focused, prefers written over verbal, avoids spotlight

**S - Steadiness (Supportive, Patient)**
- **High S indicators**: Emphasis on team/collaboration, loyalty themes, steady career progression, patient approach, supportive of others, values stability
- **Low S indicators**: Frequent role changes, comfort with change, fast-paced, independent

**C - Conscientiousness (Analytical, Detail-oriented)**
- **High C indicators**: Technical depth, analytical approach, quality focus, systematic processes, detailed explanations, credentials emphasis, cautious decisions
- **Low C indicators**: Big-picture focus, quick decisions, risk-tolerant, flexible with rules

### DISC Communication Tips by Type

| Primary Type | How to Communicate |
|--------------|-------------------|
| **High D** | Be direct, get to the point quickly, focus on results and bottom line, avoid small talk, let them feel in control |
| **High I** | Be friendly and enthusiastic, allow time for relationship building, use stories and examples, provide social recognition |
| **High S** | Be patient and supportive, provide stability and reassurance, avoid rushing decisions, show genuine interest in them |
| **High C** | Provide detailed information, be accurate and logical, give time to analyze, avoid emotional appeals, respect their expertise |

### DISC Profile HTML Template

```html
<div class="card">
    <div class="card-header">
        <h3 class="card-title">📊 DISC Personality Profile
            <span class="methodology-callout">
                <span class="methodology-icon">ℹ️</span> How assessed
                <div class="methodology-tooltip">⚠️ AI-INFERRED: DISC assessment based on observable behavioral indicators from public content, communication style, and role characteristics. This is NOT a formal DISC assessment - use as meeting preparation guidance only.</div>
            </span>
        </h3>
        <span class="badge badge-inferred">INFERRED</span>
    </div>
    <div class="grid-2">
        <div>
            <div class="disc-chart">
                <div class="disc-bar d-bar" style="height: {{DISC_D_SCORE}}%;"><span>D</span><span class="disc-score">{{DISC_D_SCORE}}</span></div>
                <div class="disc-bar i-bar" style="height: {{DISC_I_SCORE}}%;"><span>I</span><span class="disc-score">{{DISC_I_SCORE}}</span></div>
                <div class="disc-bar s-bar" style="height: {{DISC_S_SCORE}}%;"><span>S</span><span class="disc-score">{{DISC_S_SCORE}}</span></div>
                <div class="disc-bar c-bar" style="height: {{DISC_C_SCORE}}%;"><span>C</span><span class="disc-score">{{DISC_C_SCORE}}</span></div>
            </div>
            <div class="disc-labels">
                <span>Dominance</span>
                <span>Influence</span>
                <span>Steadiness</span>
                <span>Conscientiousness</span>
            </div>
        </div>
        <div>
            <div class="disc-primary">Primary: <strong>{{DISC_PRIMARY_TYPE}}</strong></div>
            <div class="disc-secondary">Secondary: {{DISC_SECONDARY_TYPE}}</div>
            <p class="disc-description">{{DISC_DESCRIPTION}}</p>
        </div>
    </div>
    <div class="insight-box blue" style="margin-top: 16px;">
        <div class="insight-title">💬 Communication Tips:</div>
        <p>{{DISC_COMMUNICATION_TIPS}}</p>
    </div>
</div>
```

### DISC Chart CSS (add to template styles)

```css
.disc-chart { display: flex; align-items: flex-end; justify-content: space-around; height: 150px; padding: 10px; background: #f8f9fa; border-radius: 8px; }
.disc-bar { width: 50px; display: flex; flex-direction: column; align-items: center; justify-content: flex-end; border-radius: 4px 4px 0 0; min-height: 20px; color: white; font-weight: 600; padding: 8px 0; }
.disc-bar span { font-size: 0.9rem; }
.disc-score { font-size: 0.75rem; opacity: 0.9; }
.d-bar { background: linear-gradient(180deg, #dc2626, #ef4444); }
.i-bar { background: linear-gradient(180deg, #f59e0b, #fbbf24); }
.s-bar { background: linear-gradient(180deg, #16a34a, #22c55e); }
.c-bar { background: linear-gradient(180deg, #2563eb, #3b82f6); }
.disc-labels { display: flex; justify-content: space-around; font-size: 0.7rem; color: var(--slate-gray); margin-top: 8px; }
.disc-primary { font-size: 1.1rem; margin-bottom: 8px; }
.disc-secondary { font-size: 0.9rem; color: var(--slate-gray); margin-bottom: 12px; }
.disc-description { font-size: 0.9rem; line-height: 1.6; }
```

## Important Rules

1. **No fabrication**: If data cannot be found, use "Not publicly available"
2. **Mark confidence levels**: VERIFIED, INFERRED, or SPECULATIVE badges
3. **LinkedIn limitations**: Note when profile data is limited
4. **Tailor to meeting**: Engagement Playbook should be specific to the stated purpose
5. **Connection points**: Only include if requestor provided their own context
6. **Track all sources with URLs**: Store actual URLs for clickable links in sources section
7. **Add recommendations**: For SWOT items, include interactive recommendations
8. **8-dimension radar**: Use all 8 behavioral dimensions (Data-Driven, Pragmatic, Collaborative, Structured, Action-Oriented, Ethics-Focused, Innovative, Visionary)
9. **Assets folder**: Report MUST be saved in same directory as `assets/` folder for logos to display correctly
10. **Methodology callouts**: EVERY section must have an info icon explaining data provenance
11. **Clickable sources**: ALL sources must be `<a href="URL">` tags with actual URLs, NOT `<div>` elements
12. **DISC Profile**: REQUIRED for ALL reports. Include DISC personality assessment in Behavioral Analysis tab. Score each dimension (D, I, S, C) from 0-100 based on observable behavioral indicators. Include communication tips for the primary type.
13. **EMOJIS**: Do NOT use emojis in headings, body text, or labels. EXCEPTION: Use case icons (`.use-case-icon`) and differentiator icons (`.differentiator-icon`) MUST use emojis (e.g., 📄, 🤖, ⚖️, 💡, 📊, 💰, 🛡️, 🔍). Never use text abbreviations like "DOC", "BOT", "REG" as icons.
14. **Meeting Fit Score**: REQUIRED. Include a 1-10 alignment score with ONE SENTENCE rationale in Executive Summary ring visual.
15. **Recent Activity**: REQUIRED. Include last 30-90 days activity in Subject Profile tab.
16. **Value Exchange**: REQUIRED when meeting has commercial purpose. Show what YOU can offer THEM.
17. **Influence Levers**: REQUIRED. Document what motivates their decisions in Behavioral Analysis.
18. **Contact Strategy**: REQUIRED. Include optimal channel, timing, and formality in Engagement Playbook.
19. **Source Freshness**: Note the year of each source. Flag sources older than 2 years as potentially outdated.
20. **Profile Photo**: REQUIRED. Search for and include a professional headshot URL. If not found, use initials fallback.
21. **AI Use Cases Tab**: REQUIRED. Include 6-8 AI use cases tailored to the person's role/industry. Each must have title, description, and reasoning popup.
22. **Personal Interests Matching**: ONLY if requestor name is provided. Research SEQUENTIALLY - complete ALL target research first, then research requestor separately. NEVER mix data between the two.
23. **Data Isolation**: When researching for Personal Interests Matching, the requestor's data must NEVER appear in any section other than the Personal Interests Matching card. Keep strict separation.
24. **Executive Summary Quality**: The BLUF must be 2-3 sentences MAX. Strategic Insights must be 3 items, each with a bold title and 1-2 sentence explanation. Conversation Openers must be actual verbatim questions. No verbose paragraphs.
25. **PDF Download**: Uses native `window.print()` (Save as PDF in browser). No external CDN dependencies. All tabs are shown during print. No `html2pdf.js`.
26. **Git Deploy Sequence**: Always `git pull --rebase` before pushing. Handle diverged branches gracefully. Never force push. If auth fails in headless/cowork, save locally and inform user.
27. **Multi-Language Translation**: REQUIRED. After generating the English report, produce full DE and FR translations and embed them as `{{TRANSLATIONS_JSON}}`. The report includes a language switcher button (globe icon) that cycles EN → DE → FR. Translation covers ALL content, not just UI labels.
28. **AI Use Cases Scatter Map**: REQUIRED. Include an Impact vs Feasibility scatter plot in the AI Use Cases tab with 8 numbered dots. Each dot must have a tooltip with the use case name, number, and positioning rationale specific to the company.
29. **Competitive Map Rationale**: REQUIRED. Every dot on the Competitive Positioning Matrix must include a tooltip with: company name (bold), axis values, and a 1-2 sentence rationale explaining why it's positioned there.
30. **SWOT Grid**: Use a 2x2 grid layout (not 3-column). Strengths, Weaknesses, Opportunities, and Threats each get equal space.
31. **FAB Button Group**: Buttons (Share, PDF, Language) are stacked vertically in the bottom-right corner as a FAB group. They must NOT overlap horizontally.
32. **HTML Structure**: Ensure all `<div>` tags are properly closed. Each `.card` div must be independently closed - do NOT nest card divs inside each other. Verify div balance after generating the report.
33. **Translation Generation**: The `{{TRANSLATIONS_JSON}}` placeholder MUST be replaced with actual translation data, NOT with an empty `{}`. Generate complete DE and FR translations for ALL `data-i18n` and `data-i18n-html` keys. This is a REQUIRED step, not optional.
34. **Use Case Icons**: Use case cards MUST use emoji icons (📄, 🤖, ⚖️, 💡, 📊, 💰, 🛡️, 🔍, 🏭, 🎯, etc.) in the `.use-case-icon` div. Never use text abbreviations. Similarly, differentiator boxes must use emojis.
