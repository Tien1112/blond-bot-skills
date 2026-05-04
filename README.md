# The Blond Bot — Company Skills

Portable skill library for The Blond Bot. Import these skills into any Paperclip workspace.

## Skills

| Skill | Directory | Description |
|---|---|---|
| AI Humanization | `ai-humanization-skill/` | Makes AI output sound more human |
| Anti AI Writing Style | `anti-ai-wrting-style/` | Avoids typical AI writing patterns |
| Content Style Examples | `high-performing-content/` | High-performing content patterns |
| LinkedIn Post Skill | `linkedin/` | LinkedIn post creation |
| The Blond Bot Voice | `the-blond-bot-voice/` | Brand voice guidelines |
| Browser Playwright | `browser-playwright/` | Browser automation via Playwright |

## How to import into another Paperclip workspace

### Option 1: Import the whole repo (all skills)

Once this repo is on GitHub, use the Paperclip skills import API in your target workspace:

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/TheBlondBot/blond-bot-skills"}'
```

### Option 2: Import a single skill

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/TheBlondBot/blond-bot-skills/tree/main/linkedin"}'
```

### Option 3: Assign imported skills to an agent

After importing, assign skills to agents:

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/agents/<agent-id>/skills/sync" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"desiredSkills": ["linkedin", "the-blond-bot-voice"]}'
```

## Updating skills

Edit the `SKILL.md` in the relevant directory, commit, and push. Then run `install-update` in each workspace that uses the skill:

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/<skill-id>/install-update" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{}'
```
