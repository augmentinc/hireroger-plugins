---
name: roger-inbox
description: "Use when the user asks about replies, leads who responded, or wants to answer, classify or triage conversations from Roger campaigns (email and LinkedIn)."
---

# Handle replies

- `conversations_list` returns what needs attention (counts by reply type and unread) and the conversations, filtered
  by reply type (interested, meeting, question...), unread, channel or campaign.
- `conversation_get` returns one thread with its messages; unsent drafts are marked as drafts.
- Draft an answer with `conversation_reply_generate`, show it to the user and adjust. `action_preview` then
  `conversation_reply_send` sends it: it reaches the prospect, so send once the user agrees on the final text.
- Triage with `conversation_update` (reply type, read). Setting a reply type can pause that person's sequence.
- Never promise meetings, prices or terms the user has not given you; quote the thread when unsure.
