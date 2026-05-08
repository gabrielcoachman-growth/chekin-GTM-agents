# Translation QA Agent

Reviews translated HTML landing pages for Chekin. Edits files in place. Produces a changelog.

## Supported languages
| Code | Language |
|------|----------|
| `es` | Spanish (ES) |
| `pt-pt` | Portuguese (PT-PT) |
| `it` | Italian |
| `fr` | French |
| `de` | German |
| `cs` | Czech |
| `el` | Greek |

## Usage

### Single file
```
Review this landing page and apply the translation QA agent.
File: /path/to/page.html
Language: es
Changelog: /path/to/TRANSLATION_CHANGELOG.md
```

### Folder of files
```
Review all HTML files in /path/to/folder/ using the translation QA agent.
Language: it
Changelog: /path/to/TRANSLATION_CHANGELOG.md
```

## What it does
1. Loads the language config from `languages/<lang>.md`
2. Runs a **language quality pass**: register, naturalness, industry terminology, Chekin voice, regional accuracy
3. Runs an **SEO pass**: title, meta description, H1/H2, CTAs, OG tags
4. Edits the HTML file in place (text content only — no structural changes)
5. Appends a changelog entry per file

## File structure
```
translation-qa/
  AGENT.md              ← agent instructions (read this first)
  SEO_CHECKLIST.md      ← universal SEO checklist
  README.md             ← this file
  languages/
    es.md
    pt-pt.md
    it.md
    fr.md
    de.md
    cs.md
    el.md
```

## Future: integrating into the translation step
Once the QA agent output is validated across a few pages, the language configs can be appended directly to the translation prompt so pages come out right the first time. The configs are written to be usable both as QA guidelines and as translation instructions.
