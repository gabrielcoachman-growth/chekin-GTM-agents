# Translation QA Agent

## Purpose
Review translated HTML landing pages for Chekin. Edit files in place. Produce a changelog for every change made.

---

## When to run
- After translating a landing page into a target language
- Before publishing any localized page
- On demand when a page has been manually edited and needs re-validation

---

## Inputs
- `--file <path>` — single HTML file to review
- `--folder <path>` — folder of HTML files to review (processes all .html files)
- `--lang <code>` — language code: `es`, `pt-pt`, `it`, `fr`, `de`, `cs`, `el`
- `--changelog <path>` — optional path for changelog file (default: `./TRANSLATION_CHANGELOG.md`)

---

## What this agent does NOT do
- It does not change page structure, layout, or functionality
- It does not rewrite entire sections — only fixes what is wrong
- It does not translate content that was left in English by mistake (it flags it instead)
- It does not touch code, scripts, class names, IDs, or attribute values (only visible text content and meta tags)

---

## Process

### Step 1 — Load language config
Load the appropriate config from `languages/<lang>.md` before touching any file.
The config defines: register/formality rules, industry terminology, common pitfalls, Chekin voice adaptation, and SEO patterns for that market.

### Step 2 — Scan the HTML
Read the full HTML file. Identify all visible text content:
- `<title>`, `<meta name="description">`, `<meta property="og:*">`
- All heading tags: `h1`, `h2`, `h3`, `h4`
- Body copy: `<p>`, `<li>`, `<span>`, `<div>` with visible text
- CTA buttons and links: `<a>`, `<button>`
- Form labels and placeholder text

### Step 3 — Language quality pass
Review every text element against the language config. Fix:

1. **Register violations** — wrong formality level (e.g., using "vous" where "tu" is specified, or vice versa). Apply consistently across the entire page.
2. **Unnatural phrasing** — literal word-for-word translations that no native speaker would write. Rewrite naturally.
3. **Industry terminology errors** — wrong or overly generic terms for hospitality/STR concepts. Apply the glossary from the language config.
4. **Chekin voice violations** — fix passive constructions, feature-led framing, or vague benefit claims. Apply problem-first, outcome-led framing per the voice guide.
5. **Regional errors** — vocabulary or expressions that are correct in another variant but wrong for this market (e.g., BR Portuguese in a PT-PT page).
6. **Grammar and agreement** — gender agreement, plural forms, verb conjugations.

Flag (do not translate) any text that appears to have been left in English unintentionally. Add a `<!-- QA FLAG: untranslated content -->` comment inline and note it in the changelog.

### Step 4 — SEO pass
Load `SEO_CHECKLIST.md` and evaluate:

1. **Title tag** — 50–60 characters, primary keyword near the start, reads naturally in the target language. Fix if too long, too short, or keyword-stuffed.
2. **Meta description** — 140–160 characters, includes a secondary keyword, has a clear value proposition, ends with an implicit or explicit CTA. Fix if missing any of these.
3. **H1** — one per page, contains the primary keyword naturally. Fix keyword placement if missing; do not add a second H1.
4. **H2/H3** — include secondary and related keywords naturally. Fix if headings are generic or keyword-free.
5. **CTA copy** — action verbs, specific and outcome-led. Fix generic CTAs ("Click here", "More info") to specific ones ("Automatiza el check-in", "Começa agora grátis").
6. **OG tags** — if present, should match or closely mirror the title and description. Fix if they were left in English or don't match.
7. **Keyword inference** — infer the primary keyword from the H1 and page topic. Verify it appears in: title, meta description, H1, and at least one H2. Do not force unnatural repetition.

### Step 5 — Edit in place
Apply all fixes directly to the HTML file. Preserve all formatting, indentation, and code structure. Only modify text content inside tags.

### Step 6 — Write changelog
Append to the changelog file. Use the format below.

---

## Changelog format

```markdown
## [filename] — [lang] — [date]

### Language fixes
- [element] | Original: "..." | Fixed: "..." | Reason: [brief reason]

### SEO fixes
- [element] | Original: "..." | Fixed: "..." | Reason: [brief reason]

### Flags (requires manual review)
- [line ~N] | "..." | Issue: [description]
```

One entry per file. If no changes were needed, write: `## [filename] — [lang] — [date] — No changes required.`

---

## Quality bar
Every edited page should pass this check before the agent finishes:
- [ ] A native speaker of the target language would not notice this was translated
- [ ] The page register is consistent from top to bottom
- [ ] The primary keyword appears naturally in title, meta description, and H1
- [ ] Every CTA is action-led and outcome-specific
- [ ] No English text remains unless it is a brand name, product name, or code
