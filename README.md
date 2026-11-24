# Antigravity Resets MCP Server

Read-only verified facts about Google Antigravity global quota resets, dated X announcement history, and official limit rules, served by [Antigravity Resets](https://antigravityreset.online/) over the Model Context Protocol (MCP).

- **Endpoint:** `https://antigravityreset.online/mcp`
- **Transport:** Streamable HTTP, JSON-RPC 2.0 (`2025-06-18` / `2025-03-26`). `POST` only (`GET` returns HTTP `405`).
- **Authentication:** None. No API key, no sign-up, no Google account access.
- **License & Attribution:** Open dataset under CC BY 4.0 — credit [antigravityreset.online](https://antigravityreset.online/).
- **Discovery & Docs:** [Web Tracker](https://antigravityreset.online/) · [Timeline](https://antigravityreset.online/timeline/) · [Limits & Fixes](https://antigravityreset.online/limits/) · [MCP Server Card](https://antigravityreset.online/.well-known/mcp/server-card.json) · [llms.txt](https://antigravityreset.online/llms.txt) · [JSON API](https://antigravityreset.online/api/latest.json)

This repository holds client setup snippets and directory manifests for the hosted remote MCP server. Nothing needs to be installed or run locally.

> Independent community project, not affiliated with Google. "Google", "Antigravity", and "Gemini" are trademarks of Google LLC.

## Tools

All three tools are strictly read-only (`readOnlyHint: true`, `destructiveHint: false`, `idempotentHint: true`) and read the same verified dataset as the public JSON API at `antigravityreset.online`.

| Tool | Description | Arguments |
|---|---|---|
| `get_latest_reset` | Latest verified global quota reset announced on X (`@_mohansolo` / team), elapsed days since that reset, active watch banner (if any), and historical cadence stats. Does not predict future resets. | `locale` (`en` \| `zh` \| `ja` \| `ko`, default `en`) |
| `get_reset_timeline` | Verified global reset history since May 2026, newest first, each entry linked to its primary X announcement URL and interval gap. | `model`, `reason`, `from` (`YYYY-MM-DD`), `to` (`YYYY-MM-DD`), `limit` (`1–50`, default `10`), `locale` |
| `get_quota_rules` | Verified Google Antigravity Free / AI Pro / AI Ultra refresh rules, 5-hour vs 7-day weekly cap mechanics, Gemini CLI shared quota pool, and stuck-quota / Reset Onboarding fixes. | `locale` (`en` \| `zh` \| `ja` \| `ko`, default `en`) |

## Example Prompts

- "When was the last verified Google Antigravity global quota reset, and what is the X source link?"
- "List recent Google Antigravity Gemini quota resets from November 2026."
- "Why did my Antigravity quota timer jump from 5 hours to 6 days, and how do I verify `/usage`?"
- "Does Gemini CLI share the same quota pool as Google Antigravity?"

## Client Setup

### Claude Code

```bash
claude mcp add --transport http antigravity-resets https://antigravityreset.online/mcp
```

### `.mcp.json` (Claude Code / Cursor / Compatible Clients)

```json
{
  "mcpServers": {
    "antigravity-resets": {
      "type": "http",
      "url": "https://antigravityreset.online/mcp"
    }
  }
}
```

### Codex CLI (`~/.codex/config.toml`)

```toml
[mcp_servers.antigravity-resets]
url = "https://antigravityreset.online/mcp"
```

### VS Code (`.vscode/mcp.json`)

```json
{
  "servers": {
    "antigravity-resets": {
      "type": "http",
      "url": "https://antigravityreset.online/mcp"
    }
  }
}
```

### Quick `curl` Smoke Test

```bash
curl -sS -X POST https://antigravityreset.online/mcp \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"get_latest_reset","arguments":{"locale":"en"}}}'
```

## Public Data Feeds

If you prefer plain HTTP without MCP:

- Latest status JSON: `https://antigravityreset.online/api/latest.json`
- Full timeline JSON: `https://antigravityreset.online/api/timeline.json`
- Flat CSV (CC BY 4.0): `https://antigravityreset.online/data/antigravity-resets.csv`
- Atom feed: `https://antigravityreset.online/feed.xml`
