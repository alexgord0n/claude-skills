# claude-skills

A collection of skills and project instructions for Claude, built for the Gainsight SC (Solutions Consultant) team.

## Structure

```
claude-skills/
├── README.md
├── project-instructions/
│   └── gainsight-sc-assistant.md
└── skills/
    └── prospect-research/
        └── SKILL.md
```

## Skills

### prospect-research
Produces a full account dossier + visual summary card before any prospect call. Pulls from:
- Web research (company, products, news, competitors, platforms, attendees)
- Google Calendar (upcoming meeting, external attendees)
- Gmail (prior communications)
- Google Drive (existing decks and assets)
- Notion (internal meeting notes, recordings, deal pages)
- Slack (internal account conversations)
- Opine (deal intelligence and CRM context)

**Trigger:** Say "I need to learn more about my prospect"

## Usage

### Claude.ai
1. Install `prospect-research.skill` via Settings > Skills
2. Paste `project-instructions/gainsight-sc-assistant.md` content into your Project Instructions

### Claude Code
1. Copy `project-instructions/gainsight-sc-assistant.md` content into `~/.claude/CLAUDE.md`
2. Copy `skills/prospect-research/SKILL.md` to `~/.claude/skills/prospect-research/SKILL.md`

