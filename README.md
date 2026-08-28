# VersionPill MCP

Product memory for coding agents. The terminal builds; VersionPill remembers the product.

This repository is **connector metadata** for host directories (Claude, Grok, Cursor, ChatGPT, the official MCP registry). The server is hosted. Nothing here is the backend source.

- **MCP URL:** `https://mcp.versionpill.com/mcp`
- **Connect:** [versionpill.com/connect](https://versionpill.com/connect)
- **Privacy:** [versionpill.com/privacy](https://versionpill.com/privacy)
- **App:** [versionpill.com](https://versionpill.com)

## Connect

Paste the URL only. Hosts that speak OAuth open a browser. Sign in, pick a workspace, Authorize once.

```json
{
  "mcpServers": {
    "versionpill": {
      "url": "https://mcp.versionpill.com/mcp"
    }
  }
}
```

| Host | Path |
|------|------|
| Claude | Settings → Connectors → Add custom connector |
| Grok | [grok.com/connectors](https://grok.com/connectors) → New Connector → Custom |
| Cursor | Settings → MCP → Add server |
| ChatGPT | Developer mode → add connector |

Do not use Convex `.site` / `.cloud` URLs or `/sse`. Streamable HTTP on `/mcp` is the only public endpoint.

API keys (`vp_…`) are an advanced fallback for scripts. Prefer OAuth.

## What the agent can do

Read the board, open a known card, move work, import a tree, comment, draft a ship note. Default profile is board (lean). `?profile=exec` is smaller for known-card coding. `?profile=readonly` cannot write.

## Registry

Published as `io.github.versionpill/mcp`. On version tag, GitHub Actions runs `mcp-publisher`.

## License

MIT applies to the metadata and docs in this repo only. The hosted server is proprietary.
