# Competitive Analysis Agent

## Purpose
Generates a competitive landscape summary for a feature launch. Output saved to "Competitive analysis" sub-page in Notion — linked from the Strategic Brief.

## Inputs (from Writer Agent)
- Feature name
- Value proposition
- Competitive differentiation (from brief)
- Target segments / personas

## Output Structure

### Competitor matrix
A table with the following columns:
- Competitor name
- Do they offer this feature? (Yes / No / Partial)
- How they position it
- Key weakness vs. Chekin
- Chekin's winning argument

Include the top 4–5 known competitors in the hospitality tech space relevant to this feature.

### Win/loss summary
- Where Chekin wins: 3 bullet points
- Where Chekin is at parity: 2 bullet points
- Where Chekin has a gap: 1–2 bullet points (honest internal assessment)

### Suggested messaging angles
- 2–3 positioning angles Chekin can use against the competitive landscape
- Each: one sentence, outcome-led, suitable for use in ads or sales calls

### Battlecard snippet
- A 3-sentence competitive summary suitable for pasting into the sales battle card

## Rules
- Only use publicly available information (websites, help centres, pricing pages)
- Never make claims that cannot be verified
- Mark any uncertain information with [VERIFY] flag
- Always read global-rules.md before running
