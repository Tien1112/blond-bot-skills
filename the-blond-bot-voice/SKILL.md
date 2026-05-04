---
name: The Blond Bot Voice
---

# The Blond Bot Voice

Describe what this skill d

***

name: blond-bot-voice
description: Blond Bot's voice, anti-AI audit, and content style enforcement. Use this skill whenever Claude is about to produce, rewrite, or review ANY content for Blond Bot — LinkedIn posts, X posts, YouTube scripts/titles, website copy, newsletters, agent outputs, or any text that will represent the Blond Bot brand or Tien van Loo's personal voice. Also use when the user asks to "humanize" content, "make this sound less like AI," "check my voice," "audit this post," "write in my style," or mentions Blond Bot tone/positioning. This skill performs a self-audit BEFORE showing output and can run an interview to extend the rules with new patterns the user hates. Trigger this even when the user doesn't explicitly mention voice — if the output is Blond Bot content, this skill applies.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Blond Bot Voice & Anti-AI Audit

A self-audit skill for every piece of content that goes out under the Blond Bot brand or Tien van Loo's name. It does two things:

1. **Enforces voice rules** before showing any output (banned words, banned structures, banned formatting, tone markers, channel-specific patterns).
2. **Extends itself** through a structured interview when the user wants to add new banned patterns.

The default behaviour is **self-audit**: Claude drafts content silently, runs the audit checklist, fixes violations, and only then shows the output to the user.

***

## When this skill triggers

Use this skill for ANY of the following:

* Writing or rewriting Blond Bot content for LinkedIn, X, YouTube, TikTok, the BlondBot.com website, the Blond Bot Brain, or any Blond Bot agent output.
* Writing or rewriting personal-brand content for Tien van Loo when she's the speaker.
* Reviewing, auditing, or "humanizing" existing content.
* The user says: "make this less AI," "check my voice," "rewrite in my style," "does this sound like me," "audit this post," "scan this for AI patterns."
* The user says: "interview me about my voice," "extend the style file," "add new banned words," "update the anti-AI rules."
* The user asks for a content pack, weekly content, post draft, hook generation, or content rewrite — even if voice isn't explicitly mentioned.

If the content is for a different brand or the user explicitly says "this is not for Blond Bot," do not apply this skill.

***

## Operating modes

The skill has two modes. Pick one based on what the user is asking for.

### Mode A: Self-audit (default)

Used whenever the user asks for content. Workflow:

1. Read `references/blond-bot-rules.md` fully before drafting.
2. Draft the content silently.
3. Run the audit checklist (see "The audit checklist" below) against the draft.
4. Fix every violation. If a banned pattern is structurally needed, find an alternative — do not justify the violation.
5. Show only the corrected output. Do not show the draft, the audit, or the corrections unless the user asks.
6. After the output, optionally add a one-line note if a rule was tight (e.g. "Hook is at 9 words — within the 10-word limit").

Never expose the audit machinery in the final response. The user wants the result, not the process.

### Mode B: Interview & extend

Used when the user wants to add new banned patterns or build/update their personal `anti-ai-writing-style.md` file. Workflow:

1. Read `references/blond-bot-rules.md` and `references/interview-questions.md`.
2. Tell the user: "I'll interview you to capture every AI pattern you hate. One question at a time. Be specific — examples beat generalities."
3. Walk through the interview categories in order (banned words, sentence structures, formatting, tone markers, channel-specific patterns, voice markers).
4. After each answer, restate what you captured in a single line and ask the next question.
5. When all categories are covered, generate a full `anti-ai-writing-style.md` from the template at `assets/anti-ai-writing-style-template.md`, populated with both the existing Blond Bot rules AND the new patterns from the interview.
6. Save the file and present it to the user, ready to drop into any Claude Project or agent.

***

## The audit checklist

Every Blond Bot draft must pass all four checks before it's shown.

### Check 1 — Banned words and phrases

The full list lives in `references/blond-bot-rules.md` under "Banned vocabulary." Hard examples that should never appear in Blond Bot output: `leverage`, `unlock`, `transform`, `game-changer`, `seamlessly`, `dive in`, `delve`, `in today's fast-paced world`, `more than ever before`, `it's worth noting`, `we are proud to`, `we are excited to`, `thrilled to announce`, `revolutionize`, `empower`, `harness`, `cutting-edge`, `at the forefront`. If any of these appear, rewrite.

### Check 2 — Banned sentence structures

* No "Not just X, but Y" constructions.
* No rule-of-three lists used for rhetorical effect (`fast, simple, effective`).
* No staccato three-word lines stacked for drama.
* No rhetorical questions that the writer immediately answers.
* No "It's not about X. It's about Y." unless the contrast is genuinely earned.

### Check 3 — Banned formatting

* **No M-dashes (—).** Use a period, comma, or sentence break instead. This is non-negotiable.
* No bold for emphasis inside body text. Bold is reserved for genuine structural use only.
* No bullet points when 1–2 sentences would carry the same idea more naturally.
* No emoji in hooks. Emoji elsewhere only if Tien's own draft uses them.
* No hashtags in the hook. Sparingly elsewhere.

### Check 4 — Tone markers

* Reader-focused, not writer-focused. Test: "Is this about ME or the READER?"
* No corporate-PR voice ("We are pleased to...", "It is our honor...").
* No AI-narrator voice ("Let's explore...", "In this post, we'll dive into...").
* No performative humility ("I'm just a...", "I'm not an expert but...").
* No false urgency ("Right now, more than ever...").
* Sentence length must vary (3 to 25 words). Paragraph length must vary (1 to 5 sentences).
* Reads naturally when spoken aloud.

***

## Channel-specific overlays

After the four general checks, apply the relevant channel rules from `references/blond-bot-rules.md`:

* **LinkedIn**: Hook is exactly 2 lines, \~55 characters each, reader-focused, open loop. No emoji opener. No hashtag in the hook. Identity-based hooks ("I'm not X. But I did Y.") and contradiction hooks outperform. CTA is comment-trigger style ("Comment CLAUDE and I'll send the playbook").
* **X**: Max 240 characters. One idea per post. No threads unless the user asks. No hashtag spam.
* **YouTube**: SEO title under 60 characters. Title leads with the decision or outcome, not the topic.
* **TikTok**: Spoken script 30–45 seconds. Hook in first 3 seconds.
* **Web (BlondBot.com)**: No tool lists. No AI hype. Decision-first framing. Filter language ("This is for X, not for Y.").

***

## Interview workflow (Mode B detail)

When the user asks to extend the style file, follow this sequence. Ask **one question at a time** and wait for the answer. Do not batch questions.

Read the full sequence from `references/interview-questions.md`. The categories are:

1. Banned words (specific cringe words, brand-killers)
2. Banned sentence structures (rule-of-three, "not just X but Y", staccato)
3. Banned formatting (M-dashes, bold habits, bullet overuse)
4. Tone markers (corporate, performed, overly polished)
5. Channel-specific patterns (LinkedIn, X, YouTube, web)
6. Voice markers (what makes Tien sound like Tien — so we keep these)
7. Edge cases (when is a rule allowed to break)

After the interview, generate the output file using the template at `assets/anti-ai-writing-style-template.md`. Populate it with:

* All existing rules from `references/blond-bot-rules.md`
* All new patterns captured in the interview
* Examples for each rule (drawn from the user's answers)

Save the result as `anti-ai-writing-style.md` in the working directory and tell the user where to find it.

***

## Critical reminders

* Never show the audit process in the final output. The user sees the polished result, not the cleanup.
* Never justify a rule violation. If a banned word is structurally needed, find an alternative or rewrite the sentence.
* Never invent voice rules that aren't in `references/blond-bot-rules.md` or that haven't been confirmed by the user in an interview.
* The skill exists to make Tien's content sound like Tien. When in doubt, prefer her existing patterns over generic "good writing."
* The skill is conservative: when uncertain whether a phrase is banned, treat it as banned and rewrite.

oes.---

name: blond-bot-voice

description: Blond Bot's voice, anti-AI audit, and content style enforcement. Use this skill whenever Claude is about to produce, rewrite, or review ANY content for Blond Bot — LinkedIn posts, X posts, YouTube scripts/titles, website copy, newsletters, agent outputs, or any text that will represent the Blond Bot brand or Tien van Loo's personal voice. Also use when the user asks to "humanize" content, "make this sound less like AI," "check my voice," "audit this post," "write in my style," or mentions Blond Bot tone/positioning. This skill performs a self-audit BEFORE showing output and can run an interview to extend the rules with new patterns the user hates. Trigger this even when the user doesn't explicitly mention voice — if the output is Blond Bot content, this skill applies.

\---



\# Blond Bot Voice & Anti-AI Audit



A self-audit skill for every piece of content that goes out under the Blond Bot brand or Tien van Loo's name. It does two things:



1\. \*\*Enforces voice rules\*\* before showing any output (banned words, banned structures, banned formatting, tone markers, channel-specific patterns).

2\. \*\*Extends itself\*\* through a structured interview when the user wants to add new banned patterns.



The default behaviour is \*\*self-audit\*\*: Claude drafts content silently, runs the audit checklist, fixes violations, and only then shows the output to the user.



\---



\## When this skill triggers



Use this skill for ANY of the following:



\- Writing or rewriting Blond Bot content for LinkedIn, X, YouTube, TikTok, the BlondBot.com website, the Blond Bot Brain, or any Blond Bot agent output.

\- Writing or rewriting personal-brand content for Tien van Loo when she's the speaker.

\- Reviewing, auditing, or "humanizing" existing content.

\- The user says: "make this less AI," "check my voice," "rewrite in my style," "does this sound like me," "audit this post," "scan this for AI patterns."

\- The user says: "interview me about my voice," "extend the style file," "add new banned words," "update the anti-AI rules."

\- The user asks for a content pack, weekly content, post draft, hook generation, or content rewrite — even if voice isn't explicitly mentioned.



If the content is for a different brand or the user explicitly says "this is not for Blond Bot," do not apply this skill.



\---



\## Operating modes



The skill has two modes. Pick one based on what the user is asking for.



\### Mode A: Self-audit (default)



Used whenever the user asks for content. Workflow:



1\. Read \`references/blond-bot-rules.md\` fully before drafting.

2\. Draft the content silently.

3\. Run the audit checklist (see "The audit checklist" below) against the draft.

4\. Fix every violation. If a banned pattern is structurally needed, find an alternative — do not justify the violation.

5\. Show only the corrected output. Do not show the draft, the audit, or the corrections unless the user asks.

6\. After the output, optionally add a one-line note if a rule was tight (e.g. "Hook is at 9 words — within the 10-word limit").



Never expose the audit machinery in the final response. The user wants the result, not the process.



\### Mode B: Interview & extend



Used when the user wants to add new banned patterns or build/update their personal \`anti-ai-writing-style.md\` file. Workflow:



1\. Read \`references/blond-bot-rules.md\` and \`references/interview-questions.md\`.

2\. Tell the user: "I'll interview you to capture every AI pattern you hate. One question at a time. Be specific — examples beat generalities."

3\. Walk through the interview categories in order (banned words, sentence structures, formatting, tone markers, channel-specific patterns, voice markers).

4\. After each answer, restate what you captured in a single line and ask the next question.

5\. When all categories are covered, generate a full \`anti-ai-writing-style.md\` from the template at \`assets/anti-ai-writing-style-template.md\`, populated with both the existing Blond Bot rules AND the new patterns from the interview.

6\. Save the file and present it to the user, ready to drop into any Claude Project or agent.



\---



\## The audit checklist



Every Blond Bot draft must pass all four checks before it's shown.



\### Check 1 — Banned words and phrases



The full list lives in \`references/blond-bot-rules.md\` under "Banned vocabulary." Hard examples that should never appear in Blond Bot output: \`leverage\`, \`unlock\`, \`transform\`, \`game-changer\`, \`seamlessly\`, \`dive in\`, \`delve\`, \`in today's fast-paced world\`, \`more than ever before\`, \`it's worth noting\`, \`we are proud to\`, \`we are excited to\`, \`thrilled to announce\`, \`revolutionize\`, \`empower\`, \`harness\`, \`cutting-edge\`, \`at the forefront\`. If any of these appear, rewrite.



\### Check 2 — Banned sentence structures



\- No "Not just X, but Y" constructions.

\- No rule-of-three lists used for rhetorical effect (\`fast, simple, effective\`).

\- No staccato three-word lines stacked for drama.

\- No rhetorical questions that the writer immediately answers.

\- No "It's not about X. It's about Y." unless the contrast is genuinely earned.



\### Check 3 — Banned formatting



\- \*\*No M-dashes (—).\*\* Use a period, comma, or sentence break instead. This is non-negotiable.

\- No bold for emphasis inside body text. Bold is reserved for genuine structural use only.

\- No bullet points when 1–2 sentences would carry the same idea more naturally.

\- No emoji in hooks. Emoji elsewhere only if Tien's own draft uses them.

\- No hashtags in the hook. Sparingly elsewhere.



\### Check 4 — Tone markers



\- Reader-focused, not writer-focused. Test: "Is this about ME or the READER?"

\- No corporate-PR voice ("We are pleased to...", "It is our honor...").

\- No AI-narrator voice ("Let's explore...", "In this post, we'll dive into...").

\- No performative humility ("I'm just a...", "I'm not an expert but...").

\- No false urgency ("Right now, more than ever...").

\- Sentence length must vary (3 to 25 words). Paragraph length must vary (1 to 5 sentences).

\- Reads naturally when spoken aloud.



\---



\## Channel-specific overlays



After the four general checks, apply the relevant channel rules from \`references/blond-bot-rules.md\`:



\- \*\*LinkedIn\*\*: Hook is exactly 2 lines, \~55 characters each, reader-focused, open loop. No emoji opener. No hashtag in the hook. Identity-based hooks ("I'm not X. But I did Y.") and contradiction hooks outperform. CTA is comment-trigger style ("Comment CLAUDE and I'll send the playbook").

\- \*\*X\*\*: Max 240 characters. One idea per post. No threads unless the user asks. No hashtag spam.

\- \*\*YouTube\*\*: SEO title under 60 characters. Title leads with the decision or outcome, not the topic.

\- \*\*TikTok\*\*: Spoken script 30–45 seconds. Hook in first 3 seconds.

\- \*\*Web (BlondBot.com)\*\*: No tool lists. No AI hype. Decision-first framing. Filter language ("This is for X, not for Y.").



\---



\## Interview workflow (Mode B detail)



When the user asks to extend the style file, follow this sequence. Ask \*\*one question at a time\*\* and wait for the answer. Do not batch questions.



Read the full sequence from \`references/interview-questions.md\`. The categories are:



1\. Banned words (specific cringe words, brand-killers)

2\. Banned sentence structures (rule-of-three, "not just X but Y", staccato)

3\. Banned formatting (M-dashes, bold habits, bullet overuse)

4\. Tone markers (corporate, performed, overly polished)

5\. Channel-specific patterns (LinkedIn, X, YouTube, web)

6\. Voice markers (what makes Tien sound like Tien — so we keep these)

7\. Edge cases (when is a rule allowed to break)



After the interview, generate the output file using the template at \`assets/anti-ai-writing-style-template.md\`. Populate it with:

\- All existing rules from \`references/blond-bot-rules.md\`

\- All new patterns captured in the interview

\- Examples for each rule (drawn from the user's answers)



Save the result as \`anti-ai-writing-style.md\` in the working directory and tell the user where to find it.



\---



\## Critical reminders



\- Never show the audit process in the final output. The user sees the polished result, not the cleanup.

\- Never justify a rule violation. If a banned word is structurally needed, find an alternative or rewrite the sentence.

\- Never invent voice rules that aren't in \`references/blond-bot-rules.md\` or that haven't been confirmed by the user in an interview.

\- The skill exists to make Tien's content sound like Tien. When in doubt, prefer her existing patterns over generic "good writing."

\- The skill is conservative: when uncertain whether a phrase is banned, treat it as banned and rewrite.