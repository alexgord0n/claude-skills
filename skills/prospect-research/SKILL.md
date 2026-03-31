---
name: prospect-research
description: Run this skill whenever someone says "I need to learn more about my prospect", asks to prep for a discovery or demo call, asks to research a company, or provides a company name and asks for a dossier, brief, or call prep. This skill produces a full account dossier plus a visual summary card combining external company research with internal signals from Gmail, Google Calendar, Google Drive, Notion, Slack, and Opine. Always run this skill when prospect or company research is requested -- even if phrased casually like "can you look into [company]", "help me prep for my call with [company]", or "what do we know about [company]".
---

# Prospect Research Skill

## Trigger
When someone says "I need to learn more about my prospect" (or similar) -- ask:
1. What company are you meeting with?
2. Is there a specific upcoming meeting or calendar invite you want me to find?

Then execute the full research workflow below. Do not wait for the user to answer question 2 before starting -- begin all research tracks immediately in parallel using just the company name.

---

## Research Architecture: Two Parallel Tracks

Run both tracks simultaneously. Surface results as they complete. Do not wait for Track B to finish before showing Track A results.

---

## Track A: External Research (Web)

Run all sections via web search. Be concise. Use markdown headers and bullets. Link sources inline.

### A1. 🏢 Company Summary
Sub-100-word description of what the company does, who they serve, and their market position.

### A2. 📦 Products
- Product names and what each does
- Are they multi-product?

### A3. 📈 Public or Private
- Publicly traded or privately held?
- If public: ticker and current stock price (search live)

### A4. 📰 Recent News (Last 60 Days)
Search for major news: funding, acquisitions, layoffs, leadership changes, product launches, partnerships. If nothing notable, say so.

### A5. 💰 Revenue Model
- How do they make money? (SaaS, consumption, services, marketplace, etc.)
- Publicly available pricing or subscription tiers -- list them if found

### A6. ⚔️ Industry and Competitors
- Industry category
- Bulleted list of direct competitors and close alternatives

### A7. ✅ Differentiators
What sets them apart from competitors? Be specific -- not generic marketing copy.

### A8. 👥 Buyer Personas
- Day-to-day users (titles and functions)
- Economic buyers and likely champions
- Common objectors (IT, Legal, Procurement)

### A9. 🗣️ CS Terminology
- What do they call their CSMs, if not "CSM"? (e.g., Partner Success Manager, Customer Advocate)
- Key terminology, buzzwords, product names, and industry vernacular to mirror in the call

### A10. 🌐 Customer-Facing Platforms
Find URLs only first. Do NOT try to identify the underlying platform yet -- just confirm whether each exists and link it. At the end, ask: "Want me to inspect the source code of each to identify what platform they're built on?"

- **LMS / Academy / Education** -- check academy.[co].com, education.[co].com, learn.[co].com
- **Community** -- check community.[co].com, forum.[co].com
- **Knowledge Base** -- check docs.[co].com, kb.[co].com, help.[co].com
- **Support Center** -- check support.[co].com
- **Ticketing** -- check for a public-facing support or ticketing portal

Mark "Not found publicly" if none found for a category.

#### Platform Identification (only if user confirms)
Fetch source of each URL found above and look for these signals:

**Community:** Khoros = `lia` prefixed elements; Salesforce = `force.com`/`lightning`; Vanilla = `vanilla` in scripts; Gainsight = `gainsight`/`inSided`; Higher Logic = `higherlogic`/`hl-`; Discourse = `discourse` in meta/scripts

**LMS:** Skilljar = `skilljar`; Docebo = `docebo`; Gainsight CE = `northpass`/`gainsight`; LearnUpon = `learnupon`; Thought Industries = `thoughtindustries`; Absorb = `absorblms`

**Support/KB:** Zendesk = `zendesk`; Salesforce = `force.com`; Freshdesk = `freshdesk`/`freshworks`; Intercom = `intercom`; Confluence = `atlassian`/`confluence`

Report per URL with confidence level.

### A11. 📅 Upcoming Events and Webinars
Search for upcoming events, webinars, or conferences. Provide direct links.

### A12. 📖 Terminology and Vernacular
Consolidated list of buzzwords, product names, and industry jargon to use in the call.

---

## Track B: Internal Signal Research

Run all of the following in parallel using connected tools. Goal: surface any existing relationship context, prior communications, internal assets, and deal intelligence before the call.

### B1. 📆 Google Calendar -- Find the Meeting
- Search Google Calendar for upcoming events matching the company name using `gcal_list_events` with `q=[company name]`
- If a matching event is found:
  - List all attendees from the invite
  - Separate internal (gainsight.com) from external attendees
  - For external attendees: name, email, title (if available in invite)
  - Note the meeting date, time, and any agenda or description in the invite
- If no matching event found: note it and skip to attendee research using any names provided by the user

### B2. 📧 Gmail -- Prior Communications
- Search Gmail for emails to/from the company domain using `gmail_search_messages` with query `from:[company].com OR to:[company].com`
- Summarize key threads: introductions, discovery notes, follow-ups, objections raised, commitments made
- Flag any open threads or unanswered emails
- Note the most recent communication date

### B3. 📁 Google Drive -- Existing Assets
- Search Google Drive for files related to the company name
- Look for: decks, proposals, discovery docs, business cases, QBRs, notes
- List each file found with title, file type, last modified date, and a direct link
- Flag anything that looks like an AE-created or CAM-created asset (proposals, account plans, exec briefs)

### B4. 📝 Notion -- Internal Meeting Notes, Recordings, and Deal Pages
- Search Notion for pages and meeting notes related to the company name using `notion-search` and `notion-query-meeting-notes`
- Look for: internal call notes, meeting recordings, deal pages, discovery summaries, strategy docs, and QBRs
- Summarize key takeaways: pain points discussed, products mentioned, stakeholders involved, commitments made, open questions
- Flag any action items or documented next steps
- Note last updated date and link to source pages where available

### B5. 💬 Slack -- Internal Conversations
- Search Slack (public and private) for messages mentioning the company name using `slack_search_public_and_private`
- Look for: account channels (e.g., #acct-[company]), deal discussions, AE or CSM comments, escalations, or strategy threads
- Summarize key context -- what is the internal team saying about this account?

### B6. 🎯 Opine -- Deal Intelligence
- Search Opine for the deal using `find_deal_by_company_name`
- If a deal is found, pull:
  - Deal stage and sales process
  - Deal summary (set `includeSummary: true`)
  - Any notes, evaluations, or tickets on the deal
- This is the closest thing to CRM context -- prioritize surfacing deal stage and any documented pain points or objections

---

## Attendee Research

Once external attendees are identified (from calendar invite or user-provided names):

For each external attendee:
1. Web search: "[Name] [Company]" and "[Name] [Company] LinkedIn"
2. Report:
   - Current title and function
   - Likely role in the deal (economic buyer, champion, end user, IT/security, exec sponsor)
   - Any notable background, tenure, or public activity relevant to the call
3. Note: LinkedIn data comes from public web search results, not direct LinkedIn API access

Format as a table or per-person bulleted list.

---

## Output Format

Produce two outputs automatically, back to back, for every research run.

---

### Output 1: Full Account Dossier

Deliver as a structured markdown dossier with three clearly labeled sections. Use emoji section headers throughout for scannability.

**Section 1: External Research (Track A)**
All A1-A12 sections in order with emoji headers.

**Section 2: Internal Signals (Track B)**
All B1-B6 sections in order with emoji headers. If a source returned nothing, note it briefly -- absence of signal is useful context.

**Section 3: Attendee Profiles**
One entry per external attendee.

Keep each section tight. No filler. Link everything possible.

---

### Output 2: Visual Summary Card

After the full dossier, automatically generate a visual HTML summary card using the Artifact/visualizer. Do not wait to be asked.

The visual summary is a single-screen card the SC can reference at a glance during the call. Build it as an HTML artifact with the following layout:

**Header Bar**
- Company name + call type (e.g., "Discovery Call", "Product Overview", "Cross-Sell Demo")
- Meeting date, time, and duration
- Tag badge for deal type (e.g., "New Logo", "Cross-Sell", "Expansion", "Renewal")

**Key Metrics Row** (4 stat blocks)
- ARR (existing GS ARR if customer, or deal size if prospect)
- Company valuation or funding stage
- Scale metric (users, seats, orgs -- whatever is most relevant)
- Contract end or timeline urgency (if known)

**Deal Timeline** (if internal signals found it)
- Chronological list of key deal milestones with dates
- Highlight the upcoming call as the current step

**Competitive Status** (if competitors identified)
- One row per active or eliminated competitor
- Color-coded status badge: green = eliminated, yellow = still active, red = preferred

**Attendee Cards**
- One card per external attendee
- Name, title, RSVP status (Accepted / No RSVP / Not on invite)
- 2-3 sentence coaching note: their likely agenda, what to focus on, what to avoid
- Role tag badge (Champion / Economic Buyer / Operator / Admin / Exec Sponsor)

**Documented Requirements** (if found in internal signals)
- Bulleted checklist of confirmed requirements from prior calls or emails

**Pre-Call Flags**
- Surface any risks, gaps, or critical action items from the research
- Color-coded by severity: red = Critical, yellow = Gap, blue = In Progress
- Keep to 4-5 max -- most important only

**Design notes:**
- Clean, card-based layout. Dark header, white content cards, color-coded badges.
- Readable at a glance. No walls of text.
- If data is missing for any section, omit that section rather than showing empty placeholders.
- If Opine or internal signals found deal stage, surface it prominently in the header.

---

The goal: SC reads the dossier once for depth, glances at the visual card during the call for quick reference.
