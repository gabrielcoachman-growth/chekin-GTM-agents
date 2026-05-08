# SEO Checklist — Translation QA

Universal SEO structure requirements for all Chekin landing pages, regardless of language.
Language-specific SEO patterns (search intent, keyword phrasing) are in each `languages/<lang>.md` file.

---

## Title tag
- Length: 50–60 characters (including spaces)
- Primary keyword: in the first 40 characters where possible
- Brand name: include "Chekin" if it fits naturally; omit if it pushes the title over 60 characters
- Format: `[Primary keyword] — [Value prop] | Chekin` or `[Primary keyword]: [Value prop]`
- Must read as a natural sentence or phrase in the target language — not a keyword list
- No ALL CAPS, no excessive punctuation

## Meta description
- Length: 140–160 characters
- Must include: primary keyword + one secondary keyword or related term
- Must include: a clear value proposition (what does the user get?)
- Must end with: an implicit or explicit action ("Pruébalo gratis", "Descubra como", "Jetzt starten")
- No keyword stuffing — reads as a human-written sentence
- Avoid starting with "We" or the brand name — lead with the user benefit

## H1
- Exactly one per page
- Contains the primary keyword — naturally, not forced
- Outcome-led where possible: what does the user achieve, not what the product does
- 40–70 characters ideally
- Never identical to the title tag (can be similar but not a copy)

## H2 / H3
- Each H2 should target a secondary keyword or a variation of the primary
- H3s support the H2 above them — no need to force keywords into every H3
- Avoid generic H2s: "Features", "Benefits", "How it works" — replace with specific outcome-led variants
  - BAD: "Features" → GOOD: "Everything you need to automate guest check-in"
  - BAD: "How it works" → GOOD: "Up and running in 15 minutes"

## CTA copy
- Always use an action verb: automate, start, discover, get, try
- Be specific about the outcome: not "Learn more" but "See how it works in 2 minutes"
- Primary CTA (above the fold): highest-intent, outcome-specific
- Secondary CTAs: can be softer but still action-led
- Avoid: "Click here", "More info", "Submit", "Send"

## OG / Social meta tags
- `og:title` — can match the page title or be a slightly more conversational version
- `og:description` — can match meta description or be shortened for social context
- Both must be in the target language — never leave in English
- `og:image` alt text (if present) should also be translated

## Keyword inference rules (when no keywords are provided)
1. Read the H1 — this is the primary keyword signal
2. Read all H2s — these signal secondary and related keywords
3. Infer search intent: is the user looking to learn, compare, or buy?
4. Verify the primary keyword appears in: title, meta description, H1, and at least one H2
5. Flag if the primary keyword is missing from two or more of those four elements

## What to never do
- Do not add keywords that don't exist in the body content
- Do not repeat the same keyword phrase more than 3× in headings
- Do not rewrite body copy to force keyword density — only fix headings and meta elements
- Do not change anchor text of internal links unless they contain obvious errors
