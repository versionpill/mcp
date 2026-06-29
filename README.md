# Version Pill MCP

AI-native project management for your coding agent. 60 token-lean tools for tasks, releases, epics, cycles, docs, and ideas — with version-keyed edge caching, agent memory, and RICE backlog prioritization. Your PM buddy in Claude Code, Cursor, Windsurf, and opencode.

- **Hosted endpoint:** `https://mcp.versionpill.com/mcp`
- **Website:** [versionpill.com](https://versionpill.com)
- **Source:** the worker lives in the Snow Labs monorepo; this repo is the public home for registry metadata, docs, and issues.

## Connect

### Claude Code (`~/Library/Application Support/Claude/claude_desktop_config.json`)

```json
{
  "mcpServers": {
    "versionpill": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.versionpill.com/sse"]
    }
  }
}
```

### Claude.ai (Connectors)

Connect via **Custom Connector** with URL: `https://mcp.versionpill.com/mcp` (streamable HTTP, OAuth).

### opencode (`~/.config/opencode/opencode.json`)

```json
{
  "mcp": {
    "versionpill": {
      "type": "remote",
      "url": "https://mcp.versionpill.com/mcp",
      "oauth": {}
    }
  }
}
```

Then run `opencode mcp auth versionpill`.

### Cursor / Windsurf

Add a remote MCP server at `https://mcp.versionpill.com/sse` and complete the OAuth flow.

## Authentication

OAuth is the default (browser flow, 30-day tokens). For non-interactive use, generate an API key at versionpill.com → Settings → API Keys and send it as `Authorization: Bearer vp_…`.

## Tools at a glance

- **CRUD:** `save_X` / `get_X` / `list_X` / `delete_X` for tasks, releases, docs, epics, cycles, ideas
- **Agent intelligence:** `context` (8 modes), `brain`, `brain_dump`, `memory`, `session`, `learn`, `decision`, `planner`
- **Ops:** `prioritize`, `ship_releases`, `publish_release`, `complete_cycle`, `github`, `search`, `project_status`

## Publishing to the MCP Registry

This repo is the source of truth for registry metadata. On tag push, the
[publish workflow](.github/workflows/publish-mcp.yml) validates `server.json` and
publishes to `registry.modelcontextprotocol.io` via `mcp-publisher` (GitHub OIDC).

To publish manually:

```bash
brew install mcp-publisher
mcp-publisher validate
mcp-publisher login github
mcp-publisher publish
```

## License

MIT
