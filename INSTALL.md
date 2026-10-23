# Install chucho in your agent

Chucho finds vacation homes for the trip a traveler describes and sends them to book directly
with the host. Install the published ChatGPT plugin for bundled tools and a travel skill,
or connect the public MCP server and skill in another agent. No Chucho account or API key is required.

- ChatGPT: [Install chucho — Book Direct](https://chatgpt.com/plugins/plugin_asdk_app_6abf4cf827fc819197bfe6ccf5a61927)
- MCP server: `https://chucho.ai/mcp` (Streamable HTTP, no auth)
- Skill: https://chucho.ai/.well-known/agent-skills/chucho/SKILL.md
- Bundle (skill, MCP config and plugin manifests): https://github.com/chucho-ai/agent

## If you are an AI agent reading this

Your user wants Chucho. Set up both MCP and the skill wherever your host supports them.
Use a bundled install below when it supplies both; otherwise complete both steps separately.
Check what is already installed first, and keep going after the first successful step.

**In ChatGPT, use the [published plugin](#chatgpt).** Its installation bundles the MCP
tools and `find-vacation-home` skill. Use your host's plugin installation flow if available;
otherwise give the user the direct listing link and ask them to select **Install plugin**.
Complete any user confirmation required by the host, then verify the installed plugin.
Do not create a duplicate custom MCP plugin or a separate personal skill. Opening the
listing alone is not installation. The separate setup steps below apply to other hosts.

1. **Connect MCP**: add `https://chucho.ai/mcp` as a remote HTTP server named `chucho`
   using the matching command below. Authentication is not required.
2. **Install the skill**: install `skills/chucho` from the bundle or the skill URL above
   using your host's skill installer. The skill supplies the travel workflow; MCP supplies
   the tools. A successful MCP connection does not install the skill.
3. **Verify MCP**: start a new session if needed, confirm `search_properties` appears in
   the tool list, and run a small search, for example a home for four with a pool.
4. **Verify the skill**: confirm `chucho` appears in the host's installed skills, invoke it,
   and confirm its `SKILL.md` instructions load. Report the MCP and skill results separately.

If one capability is unavailable, report that limit and complete the supported setup.
If you can only fetch URLs, read https://chucho.ai/.well-known/agent-skills/chucho/SKILL.md
and follow its public REST instructions for this task. Reading the URL does not persist an
installed skill; say so rather than reporting installation success.

## Claude

**Claude Code**: plugin (skill + MCP server):

```sh
claude plugin marketplace add chucho-ai/agent
claude plugin install chucho@chucho
```

For a separate MCP connection: `claude mcp add --transport http chucho https://chucho.ai/mcp`.
Then install the skill with [Skills for any agent](#skills-for-any-agent).

**Claude.ai and Claude Desktop**: Settings → Connectors → Add custom connector, name `chucho`,
URL `https://chucho.ai/mcp`. Search results appear as photo cards.

## ChatGPT

[Install chucho — Book Direct in ChatGPT](https://chatgpt.com/plugins/plugin_asdk_app_6abf4cf827fc819197bfe6ccf5a61927).

The published plugin includes the Chucho MCP tools and the `find-vacation-home` skill.
Installation sets up both together; no custom MCP URL, developer mode, API key, or
separate skill-creator setup is needed.

1. Open the link above and sign in to your ChatGPT account if prompted.
2. Select **Install plugin** and complete any confirmation ChatGPT shows.
3. Start a new chat, type `@`, and select **chucho — Book Direct** from the picker.
4. Describe your trip, for example: “Find a vacation home for six people with a private
   pool” or “Ayúdame a encontrar una casa de vacaciones para mi familia.”
5. Confirm that ChatGPT uses Chucho to search and returns homes with photos, property
   details, and host booking links. If Chucho is already installed, start at step 3.

You can also find the listing by searching **chucho — Book Direct** in
[ChatGPT Plugins](https://chatgpt.com/plugins). If installation is unavailable in a
managed workspace, ask your administrator to enable the plugin.

If you previously created a personal Chucho MCP plugin or skill, select the published
**chucho — Book Direct** plugin for this setup. After verifying it works, you can remove
any duplicate personal setup you no longer use.

Chucho helps you find homes and reach their hosts. Confirm final availability, prices,
and booking terms with the host; installing or using the plugin does not make a booking.

## OpenAI Codex

```sh
codex plugin marketplace add chucho-ai/agent
```

Then open `/plugins` and install **chucho**, which bundles MCP and the skill. For separate
setup, run `codex mcp add chucho --url https://chucho.ai/mcp`, then ask `$skill-installer`
to install `skills/chucho` from `https://github.com/chucho-ai/agent`.
Start a new session and verify both the MCP tools and the `$chucho` skill.

## Gemini CLI

```sh
gemini extensions install https://github.com/chucho-ai/agent
```

For separate setup: `gemini mcp add --transport http chucho https://chucho.ai/mcp`, then
install the skill with [Skills for any agent](#skills-for-any-agent).

## Cursor

[Add chucho to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=chucho&config=eyJ1cmwiOiJodHRwczovL2NodWNoby5haS9tY3AifQ==),
or add the JSON below to `~/.cursor/mcp.json`. Then install the skill below.

## VS Code (GitHub Copilot)

[Add chucho to VS Code](vscode:mcp/install?%7B%22name%22%3A%22chucho%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A//chucho.ai/mcp%22%7D),
or run `code --add-mcp '{"name":"chucho","type":"http","url":"https://chucho.ai/mcp"}'`.
Search results appear as photo cards.
Also install the skill below if your Copilot environment supports Agent Skills.

## Skills for any agent

```sh
npx skills add chucho-ai/agent
```

This installs the `chucho` skill into Claude Code, Codex, Cursor, Gemini CLI, OpenCode and other
agents that read skills. Agents that support skill discovery can also read
https://chucho.ai/.well-known/agent-skills/index.json.
This command installs the skill; connect MCP separately if your host supports it, then
verify both components as described above.

## Any other MCP client

Goose, Windsurf, Zed, Cline, LM Studio and others accept a remote server entry. The key names
vary by client (`url`, `serverUrl` or `httpUrl`):

```json
{
  "mcpServers": {
    "chucho": { "type": "http", "url": "https://chucho.ai/mcp" }
  }
}
```

## What you get

- Vibe search: describe the trip in your own words, plus hard filters for place, guests,
  bedrooms, pool and amenities. English and Spanish.
- Photo cards in hosts that support MCP Apps (such as Claude and VS Code) and
  ready-made markdown cards everywhere else.
- Host prices and availability for exact or flexible dates, where the host's site supports it.
- Direct booking links and guest-approved enquiries to the host. Chucho never takes payment
  and never confirms a booking; the host does.

## Reference

- [Agent guide](https://chucho.ai/agents.md): REST, MCP and A2A details
- [OpenAPI](https://chucho.ai/openapi.json)
- [MCP server card](https://chucho.ai/.well-known/mcp/server-card.json)
- [llms.txt](https://chucho.ai/llms.txt)
- Privacy: https://chucho.ai/privacy/ · Support: hello@chucho.ai
