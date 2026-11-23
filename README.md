# Equall plugin marketplace

Connect your AI agent to [Equall](https://equall.com). The Equall AI agent plugin lets you find your data rooms and ask questions about published governance reports, with citations to the underlying sources.

## Installation

### ChatGPT desktop / Codex

```sh
codex plugin marketplace add https://github.com/Equall-ai/plugins
codex plugin add equall@equall
```

Sign in to your Equall account when prompted, then open a new chat with the Equall plugin selected.

### Claude Code

Add the marketplace:

```sh
claude plugin marketplace add https://github.com/Equall-ai/plugins
```

The marketplace uses Claude Code's catalog format. The Equall plugin uses the portable Agent Plugins format, which requires a client that supports `mcp.json` to load its MCP tools. Claude Code's `.mcp.json` configuration is not included.

## Using Equall

Start with a question:

- “Which Equall data rooms can I access?”
- “Who sits on the board of this company?”
- “What investor approval rights are described in this governance report?”

The plugin uses your Equall account's access permissions. Choose a data room, ask about its published governance report, and follow the citations to review the source material.

## Connection

`https://equall.com/mcp` is Equall's production MCP endpoint and OAuth resource identifier. Authentication uses your Equall account through your client's sign-in flow.

## Development

Plugins follow the [Agent Plugins specification](https://agent-plugins.org/specification). The marketplace catalog lives in `.claude-plugin/marketplace.json`, and each plugin lives under `plugins/`.

```text
.claude-plugin/marketplace.json
plugins/equall/
├── plugin.json
├── mcp.json
├── skills/equall-governance/SKILL.md
└── assets/equall.svg
```

Register a local checkout with Codex from the repository root:

```sh
codex plugin marketplace add "$PWD"
codex plugin add equall@equall
```

Validate the marketplace and check plugin discovery:

```sh
claude plugin validate --strict .
codex plugin list --marketplace equall --available --json
```

To check the live connection, sign in and ask which data rooms you can access.

## References

- [Agent Plugins specification](https://agent-plugins.org/specification)
- [OpenAI plugin packaging and marketplaces](https://developers.openai.com/plugins/build/plugins)
- [OpenAI MCP connection setup](https://developers.openai.com/plugins/deploy/connect-chatgpt)
- [Claude Code marketplace authoring](https://code.claude.com/docs/en/plugins/create-marketplace)
- [Claude Code plugin manifests](https://code.claude.com/docs/en/plugins/manifest-reference)
