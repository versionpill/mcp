---
name: versionpill
description: >
  Use the hosted VersionPill MCP board for product memory while coding.
  Triggers: board, pulse, ship, vision, "what's next", VersionPill, product cards.
---

# VersionPill — hosted board

**URL:** `https://mcp.versionpill.com/mcp`  
**Auth:** OAuth in the browser. Do not ask the user to mint a key unless the host has no OAuth.

## Ritual

1. Known card key → `get_task` then `update_task` / `move_task`. Do not list-scan.
2. Need orientation once → `get_desk_context` with `scope=pin` or `scope=pulse`.
3. Multi-step → `desk_run` (≤48). Trees → `bulk_create_tasks`.
4. Discover tools → `list_board_tools`. Do not call `tools/list` as a tool name.
5. Public ship copy stays in customer language. No ticket IDs on the public page.
6. `publish_release` is founder-gated. Draft only unless they ask to publish.

Writes return `{ok,id,k,s}`. Reuse the pin. Do not paste the full product novel into chat.
