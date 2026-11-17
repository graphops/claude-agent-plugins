# GraphOps RPC

Read EVM and Bitcoin chain data with GraphOps RPC: query blocks, balances, contract calls and event logs through the RPC MCP server, and write bounded, recoverable JSON-RPC code.

## Install

```text
/plugin marketplace add graphops/claude-agent-plugins
/plugin install graphops-rpc@graphops
```

## Set up

When you enable the plugin, Claude Code asks for a GraphOps RPC API key. Create one for the environment your agent works in, with a name that says so, so you can revoke it without affecting your applications. Requests through the MCP server use credits like any other RPC request.

To write code that calls RPC directly, set `GRAPHOPS_RPC_API_KEY` in the environment where your code runs. The skill reads the key from there and never asks you to paste it into the conversation.

## Contents

- Skill `graphops-rpc`, published at https://docs.graphops.xyz/.well-known/agent-skills/graphops-rpc/SKILL.md
- MCP server `graphops-rpc` at `https://rpc.graphops.xyz/v1/mcp`
- Requires the `graphops` plugin

The skills contain instructions and links to the live documentation, never scripts. They are generated from the GraphOps documentation; see https://docs.graphops.xyz/ai-agents for other ways to use GraphOps with AI agents.
