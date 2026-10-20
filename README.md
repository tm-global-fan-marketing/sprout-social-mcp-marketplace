# Sprout Social MCP marketplace

A plugin marketplace containing one plugin, `sprout-social`, which connects ChatGPT or Codex to the
Sprout Social MCP server (a Cloudflare Worker). The server is read-only: profiles, posts, tags and analytics.

## Add the marketplace

Codex CLI:

    codex plugin marketplace add <owner>/sprout-social-mcp-marketplace

ChatGPT desktop app: add the marketplace as a source, restart the app, open the Plugins Directory,
choose "Sprout Social", and install `sprout-social`.

## Connecting

Installing triggers OAuth. The server registers the client automatically (Dynamic Client Registration)
and shows an approval page that asks for the **approval passcode**. Get it from the server owner.

## Layout

    .agents/plugins/marketplace.json     the catalog
    plugins/sprout-social/plugin.json    plugin manifest
    plugins/sprout-social/mcp.json       the remote MCP server and its OAuth settings

## Plugin layout

The ChatGPT/Codex desktop app loads plugins from `.codex-plugin/plugin.json`, whose `mcpServers` field points at
`.mcp.json`. The root `plugin.json` / `mcp.json` are the portable copies of the same content; keep them identical.

## Authentication

`.mcp.json` carries no auth settings: the app discovers OAuth from the server's `401` challenge and registers itself
(Dynamic Client Registration).
