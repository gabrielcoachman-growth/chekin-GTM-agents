# Blog Agent

## Purpose
Generates a full blog post and a changelog entry for the feature launch. Output saved to "Blog post" sub-page in Notion.

## Inputs (from Writer Agent)
- Feature name, tier, GA date
- Problem statement
- Value proposition
- Key messages
- Before / after
- How it works (from Notion launch page)
- SEO keywords

## Output Structure
Generate in English first, then all 6 languages:

### Blog post (800–1000 words)
- SEO title (include primary keyword, under 60 characters)
- Meta description (under 155 characters, benefit-led)
- Introduction (hook with the problem, 100 words)
- Section 1: The problem (150 words)
- Section 2: How [Feature Name] solves it (200 words, outcome-led)
- Section 3: How it works — step by step (200 words)
- Section 4: Who benefits and how (150 words)
- Conclusion + CTA (100 words)
- Suggested internal links: [leave as placeholder: LINK TO RELATED FEATURE]

### Changelog entry (50–80 words)
- Format: "**[Feature Name]** — [one sentence benefit summary]. [2–3 sentences on what's new]. Available to [which plan/tier]."

## Rules
- Lead every section with outcome, not feature description
- Never use passive voice
- SEO title must include the primary keyword from the brief
- Blog post must be readable by a non-technical hotel manager
