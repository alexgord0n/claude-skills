# claude-skills

Skills and project instructions for Claude, built for the Gainsight Go-to-Market team.

## Repo Structure

```
claude-skills/
├── README.md
├── project-instructions/
│   └── gainsight-sc-assistant.md        # Paste into Claude Project Instructions
└── skills/
    └── prospect-research/
        └── SKILL.md                     # Add more skills here as new folders
```

To add a new skill: create a new folder under `skills/` with a `SKILL.md` inside it.

---

## How to Install

### Option A: Claude.ai (Recommended for most users)

1. **Download the `.skill` file** from the [Releases](https://github.com/alexgord0n/claude-skills/releases) tab or copy the raw `SKILL.md` content
2. Go to **claude.ai > Settings > Skills**
3. Click **Install skill** and upload the `.skill` file
4. Done -- the skill is now available in any conversation

To use the project instructions:
1. Open (or create) a Claude Project
2. Go to Project Settings > Instructions
3. Paste the contents of `project-instructions/gainsight-sc-assistant.md`

### Option B: Claude Code

1. Clone this repo or copy the files manually
2. Copy project instructions into your global Claude memory:
   ```bash
   cat project-instructions/gainsight-sc-assistant.md >> ~/.claude/CLAUDE.md
   ```
3. Copy each skill into your global skills folder:
   ```bash
   mkdir -p ~/.claude/skills/prospect-research
   cp skills/prospect-research/SKILL.md ~/.claude/skills/prospect-research/SKILL.md
   ```
4. Skills auto-trigger -- no manual invocation needed

---

## Skills

### prospect-research
**Trigger:** Say `"I need to learn more about my prospect"`

Produces a full account dossier + visual summary card before any prospect call. Runs two research tracks in parallel:

**External (web):** Company overview, products, funding, news, competitors, differentiators, buyer personas, CS terminology, customer-facing platforms, upcoming events

**Internal (connected tools):**
- Google Calendar -- finds the meeting and pulls external attendees automatically
- Gmail -- prior email threads with the account
- Google Drive -- existing decks, proposals, and assets from AE/CAM
- Notion -- internal meeting notes, recordings, and deal pages
- Slack -- internal account conversations and deal chatter
- Opine -- deal stage, CRM context, and documented pain points

**Output:** Full markdown dossier + auto-generated visual summary card (attendee coaching notes, deal timeline, competitor status, pre-call flags)

---

## Project Instructions

### gainsight-sc-assistant
Operating instructions for the Gainsight SC Research Assistant. Covers tone, formatting, demo philosophy, and the standing trigger for prospect research. Designed for the Enterprise/CAM SC team but generalizable to other GTM roles.

---

## Adding New Skills

1. Create a new folder: `skills/your-skill-name/`
2. Add a `SKILL.md` with YAML frontmatter (`name` and `description` required)
3. Submit a PR or push directly if you have access

Frontmatter format:
```yaml
---
name: your-skill-name
description: When to trigger this skill and what it does. Be specific -- this is what Claude reads to decide whether to use the skill.
---
```

