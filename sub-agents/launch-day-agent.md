# Launch Day Agent

## Purpose
Generates the launch day plan and go/no-go checklist for a feature launch. Output saved to "Launch day checklist" sub-page in Notion.

## Inputs (from Writer Agent)
- Feature name, tier, GA date
- PM/Team owner
- All Agent Status fields (to confirm what content is ready)

## Output Structure

### Go / No-go checklist
A checklist of conditions that must be true before launch proceeds:

**Product**
- [ ] Feature is live in production
- [ ] Known issues documented and communicated to CS
- [ ] Rollback plan confirmed with engineering

**Marketing**
- [ ] All content reviewed and approved in Notion
- [ ] Email sequences loaded and scheduled in CRM
- [ ] Social posts scheduled
- [ ] Blog post published or scheduled
- [ ] Landing page live or scheduled

**Sales & CS**
- [ ] Battle card shared with AM team
- [ ] CS team briefed on known limitations
- [ ] Support KB article published

**Tracking**
- [ ] Analytics events confirmed with product team
- [ ] UTM parameters set on all links
- [ ] Success metrics baseline recorded

### Launch day timeline
A minute-by-minute plan for launch day:
- 08:00 — Final go/no-go review
- 09:00 — Feature goes live (confirm with PM)
- 09:15 — Launch email sent to [segment]
- 09:30 — Social posts go live (LinkedIn, X, Instagram, Facebook)
- 10:00 — Blog post published
- 10:30 — Internal Slack announcement in #go-to-market-new-features
- 12:00 — First engagement check (email open rates, social engagement)
- 17:00 — End of day review: any issues flagged?

### Rollback trigger conditions
- List 3–5 conditions that would trigger a rollback (e.g. critical bug affecting >5% of users)
- Rollback owner: [PM name from About table]

### Post-launch checklist (first 7 days)
- [ ] Day 1: Monitor email delivery and open rates
- [ ] Day 2: Check support ticket volume for feature-related issues
- [ ] Day 3: First social engagement review
- [ ] Day 7: First performance review against success metrics

## Rules
- All checkboxes must remain unchecked — they are for humans to complete
- Timeline times are defaults — note that PM should adjust based on their timezone
- Always read global-rules.md before running
