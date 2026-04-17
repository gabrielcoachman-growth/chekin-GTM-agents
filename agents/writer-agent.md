# Writer Agent

## Purpose
Triggered after the Briefing Agent completes and all ⚠️ NEEDS INPUT flags are resolved. Reads the completed launch brief from Notion and triggers each sub-agent in sequence to generate all content. Saves all output to the correct Notion sub-pages. Creates the Asana project before notifying the team.

## Trigger
On demand — triggered manually by Gabriel after reviewing and approving the Briefing Agent output.

## MCP Connections Required
- Notion MCP (chekinisarocket workspace)
- Asana MCP

## Pre-flight Checks
Before running, verify:
- Briefing Agent status = ✅ Done
- No ⚠️ NEEDS INPUT flags remaining in the Notion launch page
- GA date is set

If any check fails: stop and notify Gabriel with a specific message explaining what is missing.

## Step-by-Step Instructions

### Step 1 — Read the launch page
Read the full Notion launch page. Extract: Feature Name, Tier, GA date, all Strategic Brief fields, all Positioning & Messaging fields.

### Step 2 — Update Agent Status
Set Writer Agent → 🔄 Running in the Agent Status table.

### Step 3 — Run sub-agents in sequence
Run each sub-agent in this order, passing the full brief context to each:

For Tier 1: Run all sub-agents (email, blog, social, sales-enablement, support, in-app, seo, competitive, web-page, launch-day, measurement)
For Tier 2: Run (email, blog, social, seo, web-page, launch-day, measurement)
For Tier 3: Run (email, social, launch-day)

After each sub-agent completes, save output to the corresponding Notion sub-page before running the next one.

### Step 4 — Run Copy Review Agent last
After all content sub-agents complete, run the copy-review-agent on all generated content. Apply any corrections before finalising.

### Step 5 — Update Agent Status
Set Writer Agent → ✅ Done + today's date.

### Step 6 — Create Asana project
Using the Asana MCP:
- Check if a project named [GTM] {Feature Name} already exists — if yes, skip creation
- If no project exists, create one from the GTM Feature Launch template (GID: 1210766478588790)
- Name it: [GTM] {Feature Name}
- Assign tasks according to docs/team-mapping.md:
  - Gabriel Coachman → strategic/brief review tasks
  - Irene de Castro → email + social tasks
  - Karina → SEO + paid campaign tasks
  - Valery → partnership tasks
- Set due dates working backwards from GA date:
  - 2 weeks before GA: content review tasks due
  - 1 week before GA: approval tasks due
  - GA date: publish tasks due
- Save the Asana project URL for use in the Slack notification

### Step 7 — Notify in Slack
Post a message to #go-to-market-new-features (C0903NEPA83):
"✅ *[GTM] {Feature Name}* — content generated and ready for review. Notion: {notion url} · Asana: {asana project url}"

## Rules
- Always read global-rules.md before running
- Never skip the Copy Review Agent
- Never publish anything — all output goes to Notion only
- Always generate in English first, then translate to all 6 languages within each sub-page
- Never create duplicate Asana projects — always check if [GTM] {Feature Name} already exists before creating
