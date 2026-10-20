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

## Known uncertainty

The `extensions["com.openai"].auth` block in `mcp.json` follows OpenAI's plugin docs as summarised,
but the exact schema was not available to verify. If installation fails on it, delete the `extensions`
block, reinstall, and let ChatGPT discover OAuth from the server's `401` challenge instead.
