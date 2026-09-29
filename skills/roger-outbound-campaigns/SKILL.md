---
name: roger-outbound-campaigns
description: "Use when the user wants to start, build, fill, launch, pause or review an outbound email/LinkedIn campaign in Roger: drafting the campaign, writing its sequence, adding contacts, approving the first sends, and reading results."
---

# Run an outbound campaign

## Before building
- `campaigns_list`: reuse or extend a campaign that already targets the same audience.
- `whoami` shows connected mailboxes and LinkedIn senders (a campaign needs a live sender for its channel) and the
  sequence credits left (each enrolled contact uses one).

## Build
1. `campaign_create_draft` with the offer, target companies and roles (ICP), channels and senders. Drafts send nothing.
2. `campaign_sequence_generate` has Roger write the sequence (a job; follow it with `job_get`), or set your own
   template through `campaign_update`. Show the steps to the user and keep them short.
   In a template, merge fields such as `{{firstName}}`, `{{companyName}}` or `{{senderFirstName}}` are filled per
   contact, and a descriptive slot such as `{{a recent news item about their company}}` is written from Roger's research
   of each prospect at send time, so keep those blocks as they are. Write plain text with a blank line between paragraphs.
3. `campaign_update` for schedule, senders, targeting, auto-send and auto-leads.
4. `campaign_get` (with stats and sequence) to check the whole setup before launch.

## Fill with people
- From existing contacts: `contacts_list` with filters, then `campaign_contacts_add` with their ids or tags.
- From new leads: follow the lead research skill, then add the saved contacts.
- `campaign_contacts_add` returns a job; Roger researches each person and drafts their sequence. Its preview shows who
  gets drafted, the sequence credits, and whether auto-send would mail them unreviewed.

## Launch (first contact with real people)
- `action_preview` for `campaign_start` shows who it reaches and what it costs; show the user, then `campaign_start`
  (it also resumes a paused campaign).
- Drafted sequences wait for approval unless the campaign auto-sends: `sequences_list` (each row shows the first
  step), read a few with the user, then
  `action_preview` and `sequences_approve`. Approving sends real emails and LinkedIn messages.
- If the campaign auto-sends, adding contacts or starting it reaches inboxes without another step; say so first.

## Run and adjust
- Results: `campaign_get` with stats; replies are handled with the inbox skill.
- `campaign_pause` stops sending immediately.
- Housekeeping (clone, folders, templates, autonomy, sequence edits, removing contacts, ending a campaign for good) is in
  the `outbound-admin` pack.
