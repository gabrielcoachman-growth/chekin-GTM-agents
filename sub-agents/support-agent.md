# Support Readiness Agent

## Purpose
Generates all customer support content for a feature launch. Output saved to "Support KB" sub-page in Notion.

## Inputs (from Writer Agent)
- Feature name, tier, GA date
- How it works (all fields from Notion launch page)
- Known issues and limitations
- Target segments / personas
- Value proposition

## Output Structure
Generate in English first, then all 6 languages (ES, PT, DE, FR, IT, CS):

### Knowledge base article (help centre format)
- Title: "How to use [Feature Name]" (SEO-friendly)
- Introduction (2–3 sentences: what it does and who it's for)
- Prerequisites (what the user needs before starting)
- Step-by-step guide (numbered steps, max 10)
- Troubleshooting (3–5 common issues + solutions)
- FAQ (3–5 questions)
- Related articles: [leave as placeholder: LINK TO RELATED ARTICLE]

### Support macro (canned response for CS team)
- Macro name: "[Feature Name] — General enquiry"
- Subject: "Re: Your question about [Feature Name]"
- Body (100–150 words): friendly, helpful, links to KB article, offers follow-up

### Known limitations notice
- A short internal note (bullet points) listing what the feature cannot do yet
- To be shared with CS and AM teams only — not published

### Escalation guide (internal)
- When to escalate: list of trigger conditions
- Who to escalate to: [placeholder — CS lead to fill in]
- Information to include in escalation: checklist

## Rules
- Always write for a non-technical hotel manager reading the KB article
- Always flag known issues clearly — never hide limitations
- Macro tone: warm, professional, solution-focused
- Always read global-rules.md before running
