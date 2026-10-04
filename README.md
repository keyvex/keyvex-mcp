# Keyvex MCP Server

US public financial and government disclosure data for AI agents. Congressional stock trades, SEC insider
filings, 13F and fund holdings, FEC campaign finance, lobbying, federal contracts and more: 60+ datasets from
official government sources, every record linked to the filing it came from.

Keyvex is a hosted remote MCP server. There is nothing to install or run: point your client at the URL below.

| Endpoint | Account | What you get |
|---|---|---|
| `https://mcp.keyvex.com` | none | congressional trades and SEC insider transactions, 1 year of history, 60 calls/day |
| `https://mcp.keyvex.com/pro` | free account at [keyvex.com](https://keyvex.com) | the full catalogue (64 tools) at your plan's quota and history |

Full documentation: https://keyvex.com/docs

## Connect

### Claude (claude.ai or Claude Desktop)

Settings → Connectors → **Add custom connector**. Name it `Keyvex` and use the URL `https://mcp.keyvex.com`.
With a Keyvex account, use `https://mcp.keyvex.com/pro` and sign in when Claude shows the Connect card.

### Claude Code

```bash
claude mcp add --transport http keyvex https://mcp.keyvex.com
```

With your plan's API key:

```bash
claude mcp add --transport http keyvex https://mcp.keyvex.com/pro \
  --header "Authorization: Bearer kvx_live_YOUR_KEY"
```

### Cursor

`~/.cursor/mcp.json` (or `.cursor/mcp.json` in one project):

```json
{
  "mcpServers": {
    "keyvex": {
      "url": "https://mcp.keyvex.com"
    }
  }
}
```

### Windsurf

`~/.codeium/windsurf/mcp_config.json` (note the field is `serverUrl`):

```json
{
  "mcpServers": {
    "keyvex": {
      "serverUrl": "https://mcp.keyvex.com"
    }
  }
}
```

### VS Code (GitHub Copilot Chat)

`.vscode/mcp.json` in your project (note the top-level key is `servers`):

```json
{
  "servers": {
    "keyvex": {
      "type": "http",
      "url": "https://mcp.keyvex.com"
    }
  }
}
```

### ChatGPT

Settings → Apps & Connectors → turn on **Developer mode**, then add a custom connector named `Keyvex` with the
URL `https://mcp.keyvex.com` and auth set to none. Available on paid ChatGPT plans.

### Any other MCP client

Use the Streamable HTTP transport with `https://mcp.keyvex.com`. No headers needed.

For Cursor, Windsurf and VS Code with a Keyvex plan, swap the URL for `https://mcp.keyvex.com/pro` and add
`"headers": { "Authorization": "Bearer kvx_live_YOUR_KEY" }`.

## Try it

Ask your agent: *"What are the biggest congressional trades this month?"* It should call a Keyvex tool and
answer with real filings, each linked to its source.

## Also available

- REST API: https://api.keyvex.com (send your key in an `x-api-key` header)
- Listed on the [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=keyvex)
  (`com.keyvex/keyvex`) and [Smithery](https://smithery.ai/servers/keyvex/keyvex)
- `server.json` in this repo is the registry entry

## About this repo

This repository holds the public docs and connection configs for Keyvex. The server itself is hosted by Keyvex;
its source is not published here.

Keyvex publishes public records and does not give investment advice.
Terms: https://keyvex.com/terms · Privacy: https://keyvex.com/privacy · Contact: contact@keyvex.com · X: [@Keyvex_API](https://x.com/Keyvex_API)
