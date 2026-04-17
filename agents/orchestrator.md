# Orchestrator Agent

## Purpose
Runs every morning at 8:45 AM. Checks all active GTM launches in Notion, monitors Asana project progress, and posts a daily status summary to Slack.

## Trigger
Scheduled — daily at 8:45 AM (Madrid time, Europe/Madrid timezone)

## MCP Connections Required
- Notion MCP (chekinisarocket workspace)
- Asana MCP
- Slack MCP

## Step-by-Step Instructions

### Step 1 — Find active launches
Search Notion for all pages under the Chekin Launch Playbook hierarchy that have Agent Status "Briefing Agent = ✅ Done" and "Orchestrator = ⏳ Pending" OR "🔄 Running".

For each active launch found, extract:
- Feature name
- Launch tier (from About table)
- GA date (from About table)
- PM/Team owner (from About table)

### Step 2 — Verify Asana project exists
Check if a project named [GTM] {Feature Name} already exists in Asana.
- If it exists: proceed to Step 3
- If it does NOT exist: this means the Writer Agent has not run yet — skip this launch in today's summary and add a note in the Slack message: "⚠️ [GTM] {Feature Name} — Asana project not yet created. Writer Agent may not have run."

### Step 3 — Check task status (daily)
For existing Asana projects, check:
- Any tasks due in the next 2 days → flag as urgent
- Any tasks overdue → flag as overdue
- Overall % complete

### Step 4 — Update Notion Agent Status
Update the 🤖 Agent Status table on the launch's Notion page:
- Orchestrator → 🔄 Running (at start)
- Orchestrator → ✅ Done + today's date (at end)

### Step 5 — Post Slack summary
Post to channel #go-to-market-new-features (C0903NEPA83).

Format:
```
🚀 *GTM Daily Briefing — {today's date}*

{For each active launch:}
*[GTM] {Feature Name}* — Tier {X} — GA: {date}
- ✅ {N} tasks complete
- 🔄 {N} tasks in progress
- ⚠️ {N} tasks overdue (if any)
- 🔔 Due in 48h: {task names} (if any)
[View in Asana →]({asana project url})

_Next run: tomorrow at 8:45 AM_
```

If no active launches: post "🟢 No active GTM launches today."

## Error Handling
- If Notion is unreachable: skip Notion update, still post Slack message with last known data
- If Asana is unreachable: skip task status check, flag in Slack message
- If Slack is unreachable: log error to GitHub (create an issue titled "Orchestrator: Slack delivery failed {date}")

## Rules
- Never post to any channel other than C0903NEPA83
- Always read global-rules.md before running
- Always read config/settings.md for environment variables
