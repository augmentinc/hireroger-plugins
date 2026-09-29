---
name: roger-weekly-review
description: "Use when the user asks how things are going overall, wants a weekly or monthly review, or a briefing across outbound campaigns, replies and ads."
---

# Weekly performance review

Gather everything in one `roger_query` script instead of many calls, for example:

```js
const [campaigns, inbox, ads] = await Promise.all([
  tools.campaigns_list({ limit: 50 }),
  tools.conversations_list({ limit: 20 }),
  tools.ads_report({ level: 'campaign' }),
])
return { active: campaigns.items.filter(c => c.status === 'ACTIVE'), inbox, ads }
```

(`return await roger.api()` lists the tools and inputs this connection can call; skip any the account does not have.)

Then report, in this order:
1. What changed since last time: replies (especially interested ones), meetings, spend, results.
2. What needs a decision now: sequences waiting for approval, replies waiting for an answer, ads not delivering.
3. Two or three concrete next steps, each tied to a tool the user can run or preview.
Use Roger's numbers exactly; do not estimate missing ones.
