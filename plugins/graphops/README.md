# GraphOps

Choose between GraphOps RPC, Subgraphs and Substreams, handle GraphOps API keys and error codes, and search the GraphOps documentation through its MCP server.

## Install

```text
/plugin marketplace add graphops/claude-agent-plugins
/plugin install graphops@graphops
```

## Set up

This plugin needs no API key. The docs MCP server searches and reads the GraphOps documentation, explains error codes and lists supported networks.

Install a service plugin as well for the data service your project uses: `graphops-rpc`, `graphops-subgraphs` or `graphops-substreams`. Install `graphops-platform` to manage Managed Subgraphs, Endpoint Aliases and API keys with the GraphOps CLI.

## Contents

- Skill `graphops`, published at https://docs.graphops.xyz/.well-known/agent-skills/graphops/SKILL.md
- MCP server `graphops-docs` at `https://docs.graphops.xyz/api/mcp`

The skills contain instructions and links to the live documentation, never scripts. They are generated from the GraphOps documentation; see https://docs.graphops.xyz/ai-agents for other ways to use GraphOps with AI agents.
