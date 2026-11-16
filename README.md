<p align="center"><img src="assets/logo.png" alt="Netcraft Studio" width="96" height="96"></p>

# Netcraft Studio MCP server

[Netcraft Studio](https://netcraft.studio/en) is a website builder for small service businesses. Its remote MCP server
lets Claude, ChatGPT, Cursor, VS Code and other MCP clients work on the websites in your Netcraft Studio account, after
you approve them.

[![Netcraft Studio MCP connector](https://glama.ai/mcp/connectors/studio.netcraft/netcraft-studio/badges/score.svg)](https://glama.ai/mcp/connectors/studio.netcraft/netcraft-studio)

| | |
| --- | --- |
| Endpoint | `https://netcraft.studio/api/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE and dynamic client registration |
| Scopes | `sites:read` (read only), `sites:write` (read and change) |
| Registry name | `studio.netcraft/netcraft-studio` ([official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=studio.netcraft)) |

The server is hosted by Netcraft Studio. This repository holds its public listing files only; there is nothing to
install or run.

## What an assistant can do

- **Create a site** from a few sentences about the business, or from a trade template, and follow its progress.
- **Read and edit pages**: sections, text, images, SEO titles and descriptions, and links between pages.
- **Manage collections** such as services, team members or projects, and the pages built from them.
- **Manage media**: upload images, change their descriptions, generate images.
- **Change the look**: logo, favicon, colours and the tone of the copy.
- **Publish** the site, on a `sites.netcraft.studio` address or on your own domain.

Reads are free. Changes use the AI credits of your account. Deleting a page, a section or a collection asks you to
confirm first. Buying a plan or a domain stays in the Netcraft Studio dashboard.

## Connect

You need a Netcraft Studio account. Creating one is free: <https://netcraft.studio/en/register>.

**Claude** (claude.ai or the desktop app): Settings → Connectors → Add custom connector, then paste
`https://netcraft.studio/api/mcp`.

**ChatGPT**: add a custom MCP server with the URL above and OAuth authentication.

**Claude Code**:

```sh
claude mcp add --transport http netcraft-studio https://netcraft.studio/api/mcp
```

**Cursor**: add this to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):

```json
{
  "mcpServers": {
    "netcraft-studio": { "url": "https://netcraft.studio/api/mcp" }
  }
}
```

**VS Code**: add this to `.vscode/mcp.json`:

```json
{
  "servers": {
    "netcraft-studio": { "type": "http", "url": "https://netcraft.studio/api/mcp" }
  }
}
```

The first call opens a Netcraft Studio page where you sign in and choose read only or read and change. You can
disconnect an assistant at any time from your profile, under **Connected AI assistants**.

## Files

- [`server.json`](server.json): the entry in the official MCP Registry.
- [`.mcp.json`](.mcp.json): a ready configuration for clients that read it.
- [`assets/`](assets): the logo.

## Contact

Netcraft Digital SRL, Cluj-Napoca, Romania · hello@netcraft.digital · <https://netcraft.studio/en>
