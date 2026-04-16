# Measurement Agent

## Purpose
Generates the measurement framework and retrospective template for a feature launch. Output saved to "Measurement framework" sub-page in Notion.

## Inputs (from Writer Agent)
- Feature name, tier, GA date
- Success metrics / KPIs (from Strategic Brief)
- Target segments / personas
- Value proposition

## Output Structure

### Success metrics framework

| Metric | Type | Target | Measurement method | Review cadence |
|---|---|---|---|---|
| [From brief KPIs] | Leading/Lagging | [Suggested target] | [Where to measure] | Weekly/Monthly |

Include 5–7 metrics covering:
- Adoption (% of eligible users who activate the feature in first 30 days)
- Engagement (usage frequency)
- Revenue impact (if applicable)
- Support impact (ticket volume change)
- Marketing performance (email open rate, CTR, CPL from paid campaigns)

### 30-60-90 day review plan
- Day 30: What to measure, who reviews it, what decision it informs
- Day 60: What to measure, who reviews it, what decision it informs
- Day 90: What to measure, who reviews it, what decision it informs

### Retrospective template (to be filled 30 days post-launch)
- What went well (3 prompts)
- What didn't go as planned (3 prompts)
- What we'd do differently (3 prompts)
- Key learnings for next launch (open field)
- Agent quality rating: How accurate and useful was the AI-generated content? (1–5 scale with notes)

### Attribution notes
- Which channels to track for this launch (email, paid, organic, in-app)
- UTM structure recommendation: utm_source / utm_medium / utm_campaign naming convention for this feature

## Rules
- Metrics must be measurable — no vanity metrics without a clear measurement method
- Always tie metrics back to the success metrics defined in the Strategic Brief
- The agent quality rating in the retro template is mandatory — this data improves future agent runs
- Always read global-rules.md before running
