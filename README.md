![spun.ink](assets/spun-url-primary.svg)

# spun.ink for your AI agent

Build and operate your spun.ink website from your AI agent.

spun.ink is the agent-operated website platform: we host the site, your agent runs it, and there is no dashboard — we never built one. Pages, posts, templates, navigation and forms are data, and the only interface is the MCP server at `https://spun.ink/mcp`. This repository packages that server with the `spun` skill, which teaches your agent the authoring loop: orient with `site_map`, preview with `create_preview_link`, and publish only after you approve. A bad publish is undone with `restore_revision`, then published again.

One package serves Claude, ChatGPT and Codex: `.claude-plugin/` and `.mcp.json` for Claude, the root `plugin.json` and `mcp.json` in the Agent Plugins format for OpenAI. `scripts/check-manifests` fails when the two drift apart.

## Install

### Claude

**claude.ai and Claude Desktop.** [Add to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=spun.ink&connectorUrl=https%3A%2F%2Fspun.ink%2Fmcp) opens the connector dialog with the name and URL filled in; choose Sign in now (not "No sign-in", which skips sign-in). By hand: open Customize, then Connectors, choose Add custom connector, name it `spun.ink` and enter `https://spun.ink/mcp`. Once spun.ink is listed in Claude's directory, it is one click there.

Skills in claude.ai chat need "Code execution and file creation" switched on, which is a paid-plan setting. Without it you still get the connector and all of its tools; only the skill is missing.

**Claude Code.**

```
/plugin marketplace add spun-ink/plugins
/plugin install spun@spun-ink
```

### ChatGPT and Codex

**ChatGPT.** In developer mode on the web: Settings, then Plugins, choose Create MCP App, name it `spun.ink`, enter `https://spun.ink/mcp` and choose OAuth. That connects the tools; the skill comes with the directory listing. Once spun.ink is listed in ChatGPT's plugin directory, it is one click there.

**Codex CLI.**

```
codex plugin marketplace add spun-ink/plugins
codex plugin add spun@spun-ink
codex mcp login spun
```

### The spun CLI

`spun setup` installs the same skill for your shell agent. Use one source per agent: where the plugin is installed — Claude Code or Codex — do not also run `spun setup claude` or `spun setup codex`, or the agent sees two `spun` skills. Run them only on a machine without the plugin.

## What happens on first use

The plugin adds an MCP server named `spun` (shown as spun.ink). It carries no token: the first time you connect, a spun.ink window opens in your browser, where you sign in, or create an account with a code mailed to you. In Claude Code, `/mcp` shows the `spun` server and lets you start or repeat that sign-in; in Codex, `codex mcp login spun` does the same.

To remove the plugin: `/plugin uninstall spun@spun-ink` in Claude Code, `codex plugin remove spun@spun-ink` in Codex.

## Links

- Docs and support: https://spun.ink/docs
- Privacy: https://spun.ink/legal/privacy
- Terms: https://spun.ink/legal/terms

Licensed under MIT.
