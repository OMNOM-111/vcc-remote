# Vibe Coding Control — Remote MCP

Connect your VCC account to read your own projects, tasks and development history,
record factual work, and request or retrieve owner decisions.

- Website: https://vibecodingcontrol.com
- Remote MCP: **https://vibecodingcontrol.com/mcp**
- [Support](SUPPORT.md) · [Privacy](https://vibecodingcontrol.com/privacy#en) · [Terms](https://vibecodingcontrol.com/terms#en)

This repository contains only distribution manifests, connection examples and one
workflow skill. The VCC application source and user data are not included.
An account is required. Use the normal VCC Google sign-in and OAuth consent;
there are no tokens to copy and no server to install. Remote access includes your
own current and future VCC projects. Revoke an application at
https://vibecodingcontrol.com/mcp/connections.

## Connect

[Add to Cursor](https://cursor.com/link/mcp/install?name=vcc-remote&config=eyJ1cmwiOiJodHRwczovL3ZpYmVjb2Rpbmdjb250cm9sLmNvbS9tY3AifQ%3D%3D) · [Add to VS Code](vscode:mcp/install?%7B%22name%22%3A%22vcc-remote%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fvibecodingcontrol.com%2Fmcp%22%7D)

These official install links open the editor confirmation and then the normal
OAuth sign-in. If your Markdown viewer blocks editor links, use the steps below.
Native editor installation of these links is not yet verified for this release.

| Platform | Supported connection |
|---|---|
| VS Code | MCP: Add Server → HTTP → enter the MCP URL → sign in. See `connections/vscode.json` for the equivalent configuration. |
| Cursor | Add the URL under MCP settings and complete OAuth, or install this Agent Plugins package when the public marketplace listing is approved. |
| Claude | Settings → Connectors → Add custom connector → enter the MCP URL → Connect and sign in. The public directory listing is a separate review. |
| ChatGPT | Plugins → Add custom MCP server, where available → MCP URL → OAuth/DCR. Public directory publication requires OpenAI approval. |
| Codex | Use the same OpenAI plugin when published, or the commands below for the CLI. |
| Windsurf / Devin Desktop | Cascade: add the entry in `connections/cascade.json` to the existing MCP config, then complete OAuth. Devin Local: `devin mcp add -s user vcc-remote https://vibecodingcontrol.com/mcp`, then `devin mcp login vcc-remote`. Cascade has no MCP marketplace or one-click install. |

```sh
codex mcp add vcc-remote --url https://vibecodingcontrol.com/mcp
codex mcp login vcc-remote --oauth-client-registration dcr
```

```sh
claude mcp add --transport http --scope user vcc-remote https://vibecodingcontrol.com/mcp
```

In Claude Code, open `/mcp` and complete authentication. Client UI availability
depends on the plan, workspace permissions and product version. Merge examples
into existing configuration; preserve all other servers and the local `vcc` entry.

First ask: “Show my VCC projects”, choose a project, then read its context.
Reuse existing task/run IDs and one stable idempotency key for each write and retry.

## Scope and review

Remote VCC cannot read local files, execute shell commands, verify Git or deploy.
Those local workflows require the existing installed VCC Connector. Agents cannot
approve owner gates: decisions remain on the VCC website and are bound to the
specific run and result. Receiving a decision does not execute the approved action.

`plugin.json` and `mcp.json` use Agent Plugins 1.0.0, supported by Cursor and
the common OpenAI directory. Both products use the same remote service.
There are no embedded credentials, app references or lifecycle hooks.
`server.json` is the official MCP Registry submission descriptor.

[Review scenarios and recording guide](REVIEW.md). No public marketplace
approval is implied by this repository or a ZIP download. The graphics-free
portable package is a draft for OpenAI until the publisher supplies approved icons,
verification, a reviewer account and an accessible demonstration.
