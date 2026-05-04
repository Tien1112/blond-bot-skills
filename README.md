# The Blond Bot — Complete Skills Setup

Full skill configuration for The Blond Bot Paperclip workspaces. This repo contains the 5 custom company skills plus install instructions for all 42 external GitHub skills used in the workspace (53 total, 6 Paperclip system skills excluded).

## Custom Company Skills (in this repo)

| Skill | Directory | Description |
|---|---|---|
| AI Humanization | `ai-humanization-skill/` | Makes AI output sound more human |
| Anti AI Writing Style | `anti-ai-wrting-style/` | Avoids typical AI writing patterns |
| Content Style Examples | `high-performing-content/` | High-performing content patterns |
| LinkedIn Post Skill | `linkedin/` | LinkedIn post creation |
| The Blond Bot Voice | `the-blond-bot-voice/` | Brand voice guidelines |
| Browser Playwright | `browser-playwright/` | Browser automation via Playwright |

## External GitHub Skills (install from source repos)

These 42 skills come from public GitHub repos. Install them in any new workspace:

### Marketing Skills (36 skills)
**Source:** `https://github.com/coreyhaines31/marketingskills`

Skills: ab-test-setup, ad-creative, ai-seo, analytics-tracking, aso-audit, churn-prevention, cold-email, community-marketing, competitor-alternatives, content-strategy, copy-editing, copywriting, customer-research, email-sequence, form-cro, free-tool-strategy, launch-strategy, lead-magnets, marketing-ideas, marketing-psychology, onboarding-cro, page-cro, paid-ads, paywall-upgrade-cro, popup-cro, pricing-strategy, product-marketing-context, programmatic-seo, referral-program, revops, sales-enablement, schema-markup, seo-audit, signup-flow-cro, site-architecture, social-content

### Other Skills (6 skills)

| Skill | Source repo |
|---|---|
| brainstorming | `https://github.com/obra/superpowers` |
| find-skills | `https://github.com/vercel-labs/skills` |
| frontend-design | `https://github.com/anthropics/skills` |
| persona-hr-coordinator | `https://github.com/googleworkspace/cli` |
| remotion-best-practices | `https://github.com/remotion-dev/skills` |
| web-design-guidelines | `https://github.com/vercel-labs/agent-skills` |

---

## Full Workspace Setup Guide

### Step 1: Import custom skills from this repo

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/TheBlondBot/blond-bot-skills"}'
```

### Step 2: Install marketing skills

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/coreyhaines31/marketingskills"}'
```

### Step 3: Install other external skills

```bash
for repo in \
  "https://github.com/obra/superpowers" \
  "https://github.com/vercel-labs/skills" \
  "https://github.com/anthropics/skills" \
  "https://github.com/googleworkspace/cli" \
  "https://github.com/remotion-dev/skills" \
  "https://github.com/vercel-labs/agent-skills"; do
  curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
    -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
    -H "Content-Type: application/json" \
    -d "{\"source\": \"$repo\"}"
  echo " <- $repo"
done
```

### Step 4: Assign skills to agents

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/agents/<agent-id>/skills/sync" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"desiredSkills": ["ai-humanization-skill", "the-blond-bot-voice", "linkedin"]}'
```

### Import a single skill from this repo

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/import" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"source": "https://github.com/TheBlondBot/blond-bot-skills/tree/main/linkedin"}'
```

## Updating skills

Edit the `SKILL.md` in the relevant directory, commit, and push. Then run install-update in each workspace:

```bash
curl -sS -X POST "$PAPERCLIP_API_URL/api/companies/$PAPERCLIP_COMPANY_ID/skills/<skill-id>/install-update" \
  -H "Authorization: Bearer $PAPERCLIP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{}'
```
