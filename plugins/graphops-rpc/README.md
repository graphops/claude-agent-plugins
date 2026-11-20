# GraphOps RPC

Read EVM and Bitcoin chain data with GraphOps RPC: query blocks, balances, contract calls and event logs through the RPC MCP server, and write bounded, recoverable JSON-RPC code.

## Install

```text
/plugin marketplace add graphops/claude-agent-plugins
/plugin install graphops-rpc@graphops
```

## Set up

When you enable the plugin, Claude Code asks for a GraphOps query key that includes RPC. Create one for the environment your agent works in, with a name that says so, so you can revoke it without affecting your applications, and without limits on networks or Subgraphs: the MCP server refuses a key with limits, because a tool call names its target in its arguments. Requests through the MCP server use credits like any other RPC request. The [RPC MCP server](https://docs.graphops.xyz/rpc/mcp) page describes its tools, results, errors and limits.

To write code that calls RPC directly, set `GRAPHOPS_API_KEY` to a query key that includes RPC in the environment where your code runs, or run the code with `graphops exec` from the GraphOps CLI, which sets it from your organization's stored key. The skill reads the key from there and never asks you to paste it into the conversation.

## Contents

- Skill `graphops-rpc`, published at https://docs.graphops.xyz/.well-known/agent-skills/graphops-rpc/SKILL.md
- MCP server `graphops-rpc` at `https://rpc.graphops.xyz/v1/mcp`
- Requires the `graphops` plugin

The skills contain instructions and links to the live documentation, never scripts. They are generated from the GraphOps documentation; see https://docs.graphops.xyz/ai-agents for other ways to use GraphOps with AI agents.
