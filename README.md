# Lovable MCP

The official [Model Context Protocol](https://modelcontextprotocol.io/) server for [Lovable](https://lovable.dev), an AI-powered full-stack app builder.

Connect Claude, Cursor, Codex, and other MCP-compatible clients to Lovable so they can create, edit, deploy, and manage Lovable projects through natural language.

## Endpoint

```
https://mcp.lovable.dev/mcp
```

Transport: [Streamable HTTP](https://modelcontextprotocol.io/specification/2025-06-18/basic/transports#streamable-http).

## Authentication

Two methods are supported:

1. **OAuth 2.1** — recommended. MCP clients discover the authorization server via RFC 9728 metadata at `https://mcp.lovable.dev/.well-known/oauth-protected-resource` and obtain a bearer token automatically. The token is passed as `Authorization: Bearer <token>`.
2. **API key** — pass a workspace-scoped Lovable API key as `Lovable-API-Key: lov_…`. Keys can be generated from your workspace settings.

## Install

### Claude Code

```sh
claude mcp add --transport http lovable https://mcp.lovable.dev
```

### Cursor / Windsurf / other MCP clients

Any client other than Claude or ChatGPT must pass Lovable's public OAuth client ID:

```json
{
  "lovable": {
    "type": "http",
    "url": "https://mcp.lovable.dev/mcp",
    "auth": {
      "CLIENT_ID": "6d465f583e1e4ce5801b1616f735670c"
    }
  }
}
```

## Tools

The server exposes tools across these areas:

- **Projects & workspaces** — list, create, deploy, inspect
- **Agent interaction** — send messages, retrieve responses
- **Code inspection** — diffs, file tree, file contents, edit history
- **Knowledge** — read and write project / workspace knowledge
- **Connectors** — list, add, and remove external integrations (Linear, Notion, Slack, custom MCP, …)
- **Templates & libraries** — browse template and library projects
- **File uploads** — generate upload URLs for attaching images

See the [Lovable MCP documentation](https://docs.lovable.dev/features/mcp) for the full tool reference.

## Registry

This repository hosts the [`server.json`](./server.json) entry for the [MCP registry](https://registry.modelcontextprotocol.io/).

## License

[Apache License 2.0](./LICENSE)
