---
name: roger-lead-research
description: "Use when the user wants prospects: searching Roger's people and company database, previewing matches for an ICP, finding and enriching people at target companies, and saving them as contacts."
---

# Find and save leads

## Free research first
- `companies_search` and `people_search` search Roger's database (no emails or phones, no credits). `people_search`
  also finds people at one company.
- `leads_preview_start` previews people who match an ICP; follow the job with `job_get`. Agree the target with the user
  before spending credits.
- `contacts_list` shows who is already in the account; avoid adding people twice.

## Spending lead credits
- `whoami` shows the credits left. `action_preview` shows what a call would cost before `leads_find`,
  `contacts_import` or `contact_email_reveal`; tell the user before a large run.
- `leads_find` finds and enriches the right people at a list of companies; `contacts_import` enriches a list of
  people (LinkedIn URLs or emails). Both run as a job: follow it with `job_get`, then save the people with
  `contacts_upsert` and `fromJob`. `contact_email_reveal` finds emails for up to 50 saved contacts.

## Save and organize
- `contacts_upsert` creates or updates contacts (title, company, stage, tags) or saves a finished lead job's people
  (`fromJob`). A new person needs a first name plus an email or LinkedIn URL, which is also how duplicates are
  matched. `contacts_tags_update` adds or removes tags.
- `do_not_contact_add` blocks people or whole companies from every campaign.
- Then hand the contact ids or tag to the outbound campaign skill.
