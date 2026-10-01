# spun.ink plugins

The spun.ink plugin for AI agents: the MCP server at `https://spun.ink/mcp` and the `spun` skill.
Install steps for Claude, ChatGPT and Codex are in [plugins/spun/README.md](plugins/spun/README.md).

| Path | What it is |
|---|---|
| `.claude-plugin/marketplace.json` | The `spun-ink` marketplace that Claude Code and Codex add |
| `plugins/spun/` | The plugin itself: manifest, `.mcp.json`, the skill. Claude's plugin directory reads this folder |
| `openai/` | The OpenAI directory's manifest and icon, in the Agent Plugins format |
| `scripts/check-manifests` | Fails when the two manifests differ in name, version or endpoint, or break OpenAI's limits. Runs on every push |
| `scripts/build-openai-zip` | Builds the ZIP for the OpenAI directory from `openai/` and the plugin's skill |

Every push to `main` is a new version in Claude's directory: raise `version` in both manifests.

Licensed under MIT.
