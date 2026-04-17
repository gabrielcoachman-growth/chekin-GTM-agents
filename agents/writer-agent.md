# Writer Agent

## Purpose
Triggered after the Briefing Agent completes and all critical ⚠️ NEEDS INPUT flags are resolved. Reads the completed launch brief from Notion and triggers each sub-agent in sequence to generate all content. Saves all output to the correct Notion sub-pages. Creates the Asana project before notifying the team.

## Trigger
On demand — triggered manually by Gabriel after reviewing and approving the Briefing Agent output.

## MCP Connections Required
- Notion MCP (chekinisarocket workspace)

## Pre-flight Checks
Before running, verify:
- Briefing Agent status = ✅ Done
- No ⚠️ NEEDS INPUT flags on **critical fields**: value proposition, target segments, key messages, pricing and packaging
- GA date is set

Advisory flags (competitive analysis, success metrics, proof points) do not block the run — they are noted in content where relevant with appropriate placeholders.

If any critical field check fails: stop and notify Gabriel with a specific message explaining which critical field is missing and what input is needed to unblock.

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

After each sub-agent writes its output to Notion, immediately verify the sub-page is not empty before proceeding to the next sub-agent. To verify:
- Read the Notion sub-page content
- If the sub-page is empty or contains less than 100 characters: retry running that sub-agent once
- If it fails again after retry: log it as ⚠️ FAILED in the 📋 Briefing Notes section and continue to the next sub-agent — do not stop the entire run
- If verified successfully: continue to the next sub-agent

### Step 4 — Run Copy Review Agent last
After all content sub-agents complete, run the copy-review-agent on all generated content. Apply any corrections before finalising.

### Step 5 — Completion Verification
Before marking the Writer Agent as done, read all 10 Notion sub-pages and produce a completion report:

| Sub-page | Status |
|---|---|
| Email sequences | ✅ Filled / ⚠️ Empty |
| Blog post | ✅ Filled / ⚠️ Empty |
| Social posts | ✅ Filled / ⚠️ Empty |
| Sales enablement | ✅ Filled / ⚠️ Empty |
| Support KB | ✅ Filled / ⚠️ Empty |
| In-app messaging | ✅ Filled / ⚠️ Empty |
| SEO keywords | ✅ Filled / ⚠️ Empty |
| Landing page copy | ✅ Filled / ⚠️ Empty |
| Launch day checklist | ✅ Filled / ⚠️ Empty |
| Measurement framework | ✅ Filled / ⚠️ Empty |

Write this completion report into the 📋 Briefing Notes section of the Notion launch page.

If any sub-pages are still empty after retries: attempt to fill them one more time before updating Agent Status.

### Step 6 — Update Agent Status
Set Writer Agent → ✅ Done + today's date.

### Step 7 — Create Asana project
Using the Asana REST API via Bash (curl):

1. **Read the PAT** from `~/.claude/settings.json`:
   ```
   ASANA_PAT=$(python3 -c "import json; print(json.load(open('/Users/gcoachman/.claude/settings.json'))['mcpServers']['asana']['env']['ASANA_ACCESS_TOKEN'])")
   ```

2. **Read from config/settings.md:**
   - Template GID (Asana GTM Feature Launch template GID)
   - Team GID (Asana GTM team GID)

3. **Check for duplicate** — search projects in the GTM team by name:
   ```
   curl -s "https://app.asana.com/api/1.0/projects?team={team_gid}&opt_fields=name" \
     -H "Authorization: Bearer $ASANA_PAT"
   ```
   If a project named `[GTM] {Feature Name}` already exists: skip creation, use existing project URL.

4. **Create from template** (if no duplicate):
   ```
   curl -s -X POST "https://app.asana.com/api/1.0/project_templates/{template_gid}/instantiateProject" \
     -H "Authorization: Bearer $ASANA_PAT" \
     -H "Content-Type: application/json" \
     -d '{
       "data": {
         "name": "[GTM] {Feature Name}",
         "team": "{team_gid}",
         "public": false,
         "requested_dates": [{"gid": "2", "value": "{GA_date_YYYY-MM-DD}"}]
       }
     }'
   ```
   The response contains `data.new_project.gid` — the project URL is `https://app.asana.com/0/{project_gid}/list`

5. **Save the project URL** for use in the Slack notification.

### Step 8 — Notify in Slack
Post a message to #go-to-market-new-features (C0903NEPA83):
"✅ *[GTM] {Feature Name}* — content generated. {N}/10 sub-pages filled. Notion: {notion url} · Asana: {asana project url}
{If any empty: ⚠️ {N} sub-pages need attention — check Briefing Notes in Notion}"

## Rules
- Always read global-rules.md before running
- Always read config/settings.md for environment variables (template GID, team GID)
- Never run if any critical field (value proposition, target segments, key messages, pricing and packaging) has an unresolved ⚠️ NEEDS INPUT flag
- Advisory flags (competitive analysis, success metrics, proof points) do not block the run — add a placeholder or note in the relevant content section
- Never skip the Copy Review Agent
- Never skip the Completion Verification step
- Never publish anything — all output goes to Notion only
- Always generate in English first, then translate to all 6 languages within each sub-page
- Never create duplicate Asana projects — always check before creating
