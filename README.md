# Roger for AI agents

Roger runs outbound sales and paid ads. Connect it to find and enrich leads, build and launch outbound campaigns, triage and answer replies, and launch, measure and adjust Meta ads, all from your agent.

This repository is Roger's Claude plugin: it connects Claude to Roger's hosted MCP server and adds operating skills
that show the agent how to run Roger's workflows well. You need a Roger account on an active plan.
Setup guide for every app: https://www.hireroger.com/docs/mcp

## Connect

- **Claude Code:** add this repository as a marketplace, then install the plugin:
  `/plugin marketplace add augmentinc/hireroger-plugins` then `/plugin install hireroger@hireroger`.
- **claude.ai, Claude Desktop, ChatGPT, Cursor, Codex and other MCP apps:** add the server URL
  `https://mcp.hireroger.com/mcp` (Streamable HTTP), sign in to Roger and choose what the app may do: Read, Act (the
  default), or Review first (under Advanced, for scheduled agents or team approval).
- **Headless agents:** create an API key on Roger's APIs page, turn on its agent access under Settings, AI apps, and
  send it as `Authorization: Bearer rgr_live_…`.

The package has both Claude's plugin layout (`.claude-plugin/`) and the open Agent Plugins layout (root `plugin.json`
and `mcp.json`) that ChatGPT, Codex and Cursor load; listings there come through each platform's plugin directory.

The plugin connects to `https://mcp.hireroger.com/mcp/directory`, which leaves out AI image and video generation.
`https://mcp.hireroger.com/mcp` has every tool your access level allows, including generating ad creatives.

## What the agent can do

Find and enrich leads, manage contacts, build and launch outbound email and LinkedIn campaigns, approve sequences, read
and answer replies, upload ad creatives, launch and adjust ads (Meta today) within your spend caps, and read
performance. Rarer actions come in tool packs, switched on per connection in Roger under Settings, AI apps.

Every change returns a receipt and is listed in Roger under Settings, AI apps, Activity, where you can also disconnect
an app at any time. Choosing the ad account, turning on autopilot or a daily batch, and setting the daily budget always
wait for a person in Roger.

## Data and privacy

Roger acts only inside the organization you sign in to and only with the access level you grant. Tool results come
from your own Roger account. See https://www.hireroger.com/privacy and https://www.hireroger.com/terms.

## Support

support@hireroger.com
