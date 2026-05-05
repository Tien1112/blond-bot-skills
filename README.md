# The Blond Bot — Skills Repository

All skills used by The Blond Bot Paperclip workspaces, synced from the local workspace. This repo contains 48 skills (6 custom company skills + 42 external skills cached locally).

## Skills (48 total)

### Custom Company Skills

| Skill | Directory | Description |
|---|---|---|
| AI Humanization | `ai-humanization-skill/` | Makes AI output sound more human |
| Anti AI Writing Style | `anti-ai-wrting-style/` | Avoids typical AI writing patterns |
| Content Style Examples | `high-performing-content/` | High-performing content patterns |
| LinkedIn Post Skill | `linkedin/` | LinkedIn post creation |
| The Blond Bot Voice | `the-blond-bot-voice/` | Brand voice guidelines |
| Browser Playwright | `browser-playwright/` | Browser automation via Playwright |

### Marketing Skills (from coreyhaines31/marketingskills)

ab-test-setup, ad-creative, ai-seo, analytics-tracking, aso-audit, churn-prevention, cold-email, community-marketing, competitor-alternatives, content-strategy, copy-editing, copywriting, customer-research, email-sequence, form-cro, free-tool-strategy, launch-strategy, lead-magnets, marketing-ideas, marketing-psychology, onboarding-cro, page-cro, paid-ads, paywall-upgrade-cro, popup-cro, pricing-strategy, product-marketing-context, programmatic-seo, referral-program, revops, sales-enablement, schema-markup, seo-audit, signup-flow-cro, site-architecture, social-content

### Other External Skills

| Skill | Original source |
|---|---|
| brainstorming | obra/superpowers |
| find-skills | vercel-labs/skills |
| frontend-design | anthropics/skills |
| persona-hr-coordinator | googleworkspace/cli |
| remotion-best-practices | remotion-dev/skills |
| web-design-guidelines | vercel-labs/agent-skills |

---

## Setup Guide

### Import all skills from this repo

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/Tien1112/blond-bot-skills"}'
```

### Import a single skill

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/Tien1112/blond-bot-skills/tree/main/linkedin"}'
```

### Assign skills to an agent

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/agents/<agent-id>/skills/sync" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"desiredSkills": ["ai-humanization-skill", "the-blond-bot-voice", "linkedin"]}'
```

## Updating skills

Edit the `SKILL.md` in the relevant directory, commit, and push. Then run install-update in each workspace:

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/<skill-id>/install-update" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{}'
```
