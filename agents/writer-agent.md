# Writer Agent

## Purpose
Triggered after the Briefing Agent completes and all ⚠️ NEEDS INPUT flags are resolved. Reads the completed launch brief from Notion and triggers each sub-agent in sequence to generate all content. Saves all output to the correct Notion sub-pages.

## Trigger
On demand — triggered manually by Gabriel after reviewing and approving the Briefing Agent output.

## MCP Connections Required
- Notion MCP (chekinisarocket workspace)

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

### Step 6 — Notify in Slack
Post a message to #go-to-market-new-features (C0903NEPA83):
"✅ *[GTM] {Feature Name}* — all content generated and ready for review in Notion. {link to Notion launch page}"

## Rules
- Always read global-rules.md before running
- Never skip the Copy Review Agent
- Never publish anything — all output goes to Notion only
- Always generate in English first, then translate to all 6 languages within each sub-page
