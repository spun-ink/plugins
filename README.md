![spun.ink](assets/spun-url-primary.svg)

# spun.ink for Claude

spun.ink is a website platform that your AI agent operates. There is no dashboard and we never built one: pages, posts, templates, navigation and forms are data, and the only interface is the MCP server at `https://spun.ink/mcp`. This plugin connects Claude to that server and adds the `spun` skill, which teaches Claude the authoring loop: orient with `site_map`, preview with `create_preview_link`, and publish only after you approve. A bad publish is undone with `restore_revision`, then published again.

## Install

**claude.ai and Claude Desktop.** [Add to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=spun.ink&connectorUrl=https%3A%2F%2Fspun.ink%2Fmcp) opens the connector dialog with the name and URL filled in; choose Sign in now (not "No sign-in", which skips sign-in). By hand: open Customize, then Connectors, choose Add custom connector, name it `spun.ink` and enter `https://spun.ink/mcp`. Once spun.ink is listed in Claude's directory, it is one click there.

**Claude Code.**

```
/plugin marketplace add spun-ink/plugins
/plugin install spun@spun-ink
```

**The spun CLI.** `spun setup` installs the same skill for your shell agent. Use one source per agent: in Claude Code, install the plugin and do not run `spun setup claude`; run `spun setup codex` for Codex, and `spun setup claude` only on a machine without the plugin.

Skills in claude.ai chat need "Code execution and file creation" switched on, which is a paid-plan setting. Without it you still get the connector and all of its tools; only the skill is missing.

## What happens on first use

The plugin adds an MCP server named `spun` (shown as spun.ink). It carries no token: the first time you connect, a spun.ink window opens in your browser, where you sign in or sign up. In Claude Code, `/mcp` shows the `spun` server and lets you start or repeat that sign-in or sign-up.

To remove the plugin in Claude Code: `/plugin uninstall spun@spun-ink`.

## Links

- Docs and support: https://spun.ink/docs
- Privacy: https://spun.ink/legal/privacy
- Terms: https://spun.ink/legal/terms

Licensed under MIT.
