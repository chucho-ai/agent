# chucho for AI agents

Chucho finds vacation homes for the trip a traveler describes and sends them to book directly
with the host. This repository packages Chucho's public MCP server (`https://chucho.ai/mcp`)
and its agent skill for every major harness.

**Install instructions for each agent: [INSTALL.md](INSTALL.md)** (also served at
https://chucho.ai/install.md).

| Path | For |
|---|---|
| `skills/chucho/SKILL.md` | The skill: Agent Skills format, used by every harness below |
| `.claude-plugin/`, `.mcp.json` | Claude Code plugin and marketplace |
| `plugin.json`, `mcp.json`, `.agents/plugins/` | Codex plugin and marketplace |
| `gemini-extension.json` | Gemini CLI extension |
| `server.json` | MCP Registry entry |

The MCP server is evergreen: new tools and card improvements reach every install without an
update. Plugin manifests omit versions where the harness allows it, so installs track this
repository.

This repository is generated from `agent/` in Chucho's main repository; open issues and changes
there, or email hello@chucho.ai.
