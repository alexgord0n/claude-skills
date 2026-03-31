---
name: demo-flow-builder
description: Build a tailored demo flow for a Gainsight product (PX, Community, Skilljar/CE, CS platform, Staircase AI, or Customer OS) based on pre-call research. Run this skill when someone asks to "build a demo flow", "put together a demo", "prep a demo", "create a demo outline", "what should I demo", "build me a flow for [product]", or any similar phrasing -- even casual like "what do I show them" or "how should I structure this demo". Always run this skill when a demo needs to be customized for a specific prospect. Produces a value-led, use-case-mapped demo flow in either robust (detailed) or light (extemporaneous bullet) mode, with real customer examples mapped to each section.
---

# Demo Flow Builder

## Purpose
Build a tailored, value-led demo flow for a specific prospect based on their documented use cases, pain points, and priorities from pre-call research. Every feature shown must tie back to a value the prospect will realize. No feature-dumping.

## Demo Philosophy
**Flow for every section:** Problem → Context → Show → Outcome → Why It Matters

- Lead with their pain, not the product
- Every feature should answer: "so what does that mean for [Prospect]?"
- Weave multi-product where relevant -- don't silo
- Make every stakeholder in the room feel addressed

---

## Step 1: Gather Inputs

You need two things before building a flow:

1. **Product(s) to demo** -- PX, Community (CC), Skilljar/CE, CS Platform, Staircase AI, Customer OS, or multi-product
2. **Pre-call research** -- the full dossier + visual summary from the prospect-research skill, raw notes, or both

If either is missing, ask for it before proceeding.

Also ask: **"Robust or light flow?"**
- **Robust** = full talk track, transition language, value statements per section, stakeholder callouts, customer examples with context
- **Light** = tight bullet outline, extemporaneous -- enough to jog memory without being a script

---

## Step 2: Extract Signal from Research

Before building the flow, extract and list:

- **Top 3 stated use cases or pain points** (direct quotes from dossier preferred)
- **Stakeholders in the room** and their likely agendas (from attendee cards)
- **Products/platform they're evaluating** (existing stack, competitors)
- **Known gaps or sensitivities** (flag these -- don't hide them in the flow)
- **Multi-product opportunity** (are there signals for PX + CC + CE together?)

Surface this as a quick "Demo Setup" block at the top of the output.

---

## Step 3: Map Use Cases to Demo Sections

Cross-reference the prospect's use cases against the demo flow reference files for each product. For each section:

1. **Is this section relevant to their stated priorities?** If not, deprioritize or cut it
2. **What is the specific value this feature delivers for their use case?**
3. **Which customer example fits best?** Pull from the customer examples reference

Only include sections that earn their place. A tight 30-minute demo is better than a 60-minute one.

---

## Step 4: Build the Flow

### Output Structure

```
## Demo Setup
[Prospect name, products, flow mode, key use cases, attendees, flags]

## Pre-Demo Framing (1-2 min)
[How to open -- tailor to their pain]

## [Product Section 1]
### [Area Name]
- Use case connection: [their specific pain/goal]
- What to show: [specific feature/area]
- Value statement: [outcome for them]
- Customer example: [Company] -- [what they do / why it's relevant]
- Transition: [bridge to next section]

[repeat per section]

## Wrap & Discovery Check
[What to ask at the end]
```

For **robust** mode: include full talk track language, transition sentences, stakeholder callouts, and context on why each customer example is relevant.

For **light** mode: bullets only -- 3-5 words per item, no prose. Just enough structure to run it extemporaneously.

---

## Step 5: Flag Gaps and Sensitivities

After the flow, always include a short **"Watch Out"** section:
- Known product gaps relevant to their use case
- Competitors they may be evaluating (and what to be ready for)
- Stakeholders who may push back (and on what)
- Any open questions from the dossier that need answers before the call

---

## Reference Files

Load the appropriate reference file(s) for the products in scope:

- `references/px-demo-flow.md` -- PX talk tracks, features, value callouts
- `references/cc-demo-flow.md` -- Community talk tracks, features, value callouts
- `references/ce-demo-flow.md` -- Skilljar/CE talk tracks, features, value callouts
- `references/cs-demo-flow.md` -- CS Platform talk tracks
- `references/staircase-demo-flow.md` -- Staircase AI talk tracks
- `references/customer-os-demo-flow.md` -- Customer OS multi-product flow
- `references/customer-examples.md` -- Full customer example library, organized by use case and product

Always load `references/customer-examples.md` regardless of which product you're demoing.

---

## Output Rules

- Lead every section with the prospect's use case -- not the feature name
- Every "Show:" item must have a corresponding "Value:" item
- Customer examples should feel like recommendations, not name-drops: explain *why* that customer is a good example for this specific prospect
- If robust mode: write as if the SC has never seen the flow before -- it should be runnable cold
- If light mode: write as if the SC knows the product cold -- just needs the structure and value hooks
- End every flow with 2-3 discovery questions to close the demo
