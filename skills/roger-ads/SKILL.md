---
name: roger-ads
description: "Use when the user wants to make ad creatives, launch or adjust paid ads (Meta today: Facebook and Instagram), change budgets or targeting, pause ads, or understand how their ads are performing in Roger."
---

# Create, launch and manage ads

Roger speaks one vocabulary for every ad network: campaign, ad group (Meta calls it an ad set), ad, and creative (a
reusable library item). Money is `{ amount, currency }` in the ad account's currency.

## Read the account
- `ads_report` at the level you need (account, campaign, ad group, ad, creative) for a date range: spend, impressions,
  clicks, results and cost per result. It reads Roger's synced copy (`syncedAt` says how fresh); `ads_account_sync` in
  `ads-setup` refreshes it. Quote numbers exactly; null means not measured. Ad group ids come from level `ad_group`.
- `ads_diagnose` when something is not delivering or the user asks what to change.
- `ads_autopilot_get` shows whether autopilot is on and what it did.

## Creatives
- `ads_creatives_list` shows the library (preview links expire; re-read instead of reusing old URLs).
- `ads_creative_upload` adds the user's own image or video from a URL.
- `ads_creatives_generate` makes new AI creatives, one short brief per ad (a job; follow it with `job_get`), then show
  them before launching. Production detail for each field is in the resource `roger://ads/creative-spec`. It is not
  offered on every connection.

## Launch (spends money)
- `action_preview` for `ads_launch` shows the plan, the daily budget it commits and who it reaches; show the user,
  then `ads_launch` (new campaign from library creatives) or `ads_creatives_add` (into an existing campaign or ad
  group). Spend stays inside the spend cap the user set in Roger. A launch that takes longer answers
  `state: running` with an `ad_launch` job; follow it with `job_get` and never launch again to retry.
- Targeting finer than a country: `ads_locations_search` returns the place keys (never guess them) for `places`.

## Adjust
- `ads_budget_set` (campaign or ad group), `ads_pause` and `ads_resume` (any level, several ids at once),
  `ads_target_cost_set` (the cost per result autopilot and verdicts judge against). Preview budget raises and resumes.
- `ads_targeting_set` changes who an ad group reaches; it re-enters the network's review, so confirm with the user.
- `ads_autopilot_stop` turns autopilot off. Turning it on, choosing the ad account, the daily budget and the daily batch
  are money decisions a person makes in Roger (the `ads-setup` pack).
- Brands, tracking and account setup are in `ads-setup`; floors, placement limits and rules in `ads-advanced`;
  competitor ads and research in `ads-research`.
