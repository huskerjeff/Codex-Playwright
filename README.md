# Claude Playwright Browser

A ready-to-use repository that tells **Claude Code** to install Playwright and browse the web for you. It includes `CLAUDE.md`, a project MCP server configuration, and a locked dependency installation.

## Use it with Claude Code

You need Node.js 20+ and Claude Code installed.

```bash
git clone https://github.com/huskerjeff/claude-playwright-browser.git
cd claude-playwright-browser
npm run setup
claude
```

Accept the project trust prompt and approve the `playwright` MCP server when Claude Code asks. Run `/mcp` to check its connection. If you ran setup after starting Claude Code, restart Claude Code so the server can connect.

Then ask:

> Read CLAUDE.md, verify that Playwright works, and browse the web to research [your topic]. Include links to your sources.

Or, if you have already opened the repository in Claude Code:

> Read CLAUDE.md, install Playwright, and set up browser access for me.

## How it works

- `CLAUDE.md` tells Claude how to install and use Playwright.
- `.mcp.json` registers Microsoft's Playwright MCP server with Claude Code.
- `playwright-mcp.config.json` selects headless Chromium with a fresh, isolated session.
- `package-lock.json` pins the server and its browser automation dependencies.

The browser runs on the machine or environment running Claude Code. It does not use your existing browser tabs or saved logins. To see a browser window on a machine with a desktop, change `headless` to `false` in `playwright-mcp.config.json`.

## Troubleshooting

- **Missing Linux libraries:** run `npm run setup:linux` if you can install system packages. This may require administrator privileges.
- **Browser executable missing:** rerun `npm run setup` on the machine running Claude.
- **MCP tools missing:** approve the project MCP server, restart Claude Code in this directory, and inspect `/mcp`.
- **Restricted cloud environment:** installation and browsing require outbound network access. `CLAUDE.md` includes a terminal-based fallback for environments that support scripts but cannot load MCP.
- **`ERR_CERT_AUTHORITY_INVALID` behind a corporate or cloud proxy:** configure the browser's trust store with your environment's trusted proxy CA. Keep certificate verification enabled.
- **Claude website or mobile app:** uploading these files alone does not install a browser there. Use Claude Code or another Claude environment that allows package installation and browser tools.

Upstream documentation: [Playwright MCP](https://github.com/microsoft/playwright-mcp) · [Claude Code MCP](https://code.claude.com/docs/en/mcp).
