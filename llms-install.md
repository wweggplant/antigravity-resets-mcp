# Installing Antigravity Resets MCP Server

Add the hosted read-only Streamable HTTP MCP server at `https://antigravityreset.online/mcp` to your MCP client. No API key, login, or local install is required.

- Claude Code: `claude mcp add --transport http antigravity-resets https://antigravityreset.online/mcp`
- Cursor / Windsurf / Claude Desktop (`.mcp.json`): `{"mcpServers":{"antigravity-resets":{"type":"http","url":"https://antigravityreset.online/mcp"}}}`
- Codex CLI (`~/.codex/config.toml`): `[mcp_servers.antigravity-resets]` + `url = "https://antigravityreset.online/mcp"`
- Server card: `https://antigravityreset.online/.well-known/mcp/server-card.json`
