# Web Page Agent

## Purpose
Generates landing page copy for a feature launch. Output saved to "Landing page copy" sub-page in Notion.

## Inputs (from Writer Agent)
- Feature name, tier, GA date
- Value proposition
- Key messages (3–5)
- Target segments / personas
- Before / after
- Proof points
- SEO keywords (primary keyword required)
- CTA per audience
- How it works

## Output Structure
Generate in English first, then all 6 languages (ES, PT, DE, FR, IT, CS):

### Hero section
- Headline (max 10 words, outcome-led, includes primary SEO keyword)
- Subheadline (max 20 words, expands on headline benefit)
- Primary CTA button text (max 5 words)
- Supporting trust line (max 10 words, e.g. "Used by 10,000+ properties across Europe")

### Problem section
- Section headline (max 8 words)
- 3 pain point cards: each with a short label (3 words) + 1-sentence description

### Solution section
- Section headline (max 10 words, outcome-led)
- 3–4 benefit cards: icon placeholder + label (3 words) + description (max 20 words)

### How it works section
- Section headline (max 8 words)
- 3 numbered steps: step label (max 5 words) + description (max 20 words each)

### Social proof section
- Section headline (max 6 words)
- 1 featured testimonial: [PLACEHOLDER — insert real quote post-launch]
- 2–3 stat callouts: [PLACEHOLDER — insert real data post-launch]

### FAQ section (3–5 questions)
- Questions a hotel manager would ask before adopting this feature
- Answers: max 50 words each, benefit-led

### Final CTA section
- Headline (max 10 words)
- CTA button text (max 5 words)
- Supporting line (max 15 words)

## Rules
- Every headline must be outcome-led — never start with the feature name
- No jargon
- SEO primary keyword must appear in hero headline and page title
- Placeholders for proof points and testimonials must be clearly marked
- Always read global-rules.md before running
