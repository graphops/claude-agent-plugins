# GraphOps Subgraphs

Query indexed blockchain entities with GraphOps Subgraphs: read schemas, freshness and query results through the Subgraphs MCP server, and write paginated GraphQL code.

## Install

```text
/plugin marketplace add graphops/claude-agent-plugins
/plugin install graphops-subgraphs@graphops
```

## Set up

When you enable the plugin, Claude Code asks for a GraphOps query key that includes Subgraphs. Create one for the environment your agent works in, with a name that says so, so you can revoke it without affecting your applications, and without limits on networks or Subgraphs: the MCP server refuses a key with limits, because a tool call names its target in its arguments. Queries through the MCP server use credits like any other Subgraphs query. The [Subgraphs MCP server](https://docs.graphops.xyz/subgraphs/mcp) page describes its tools, results, errors and limits.

To write code that calls Subgraphs directly, set `GRAPHOPS_API_KEY` to a query key that includes Subgraphs in the environment where your code runs, or run the code with `graphops exec` from the GraphOps CLI, which sets it from your organization's stored key. The skill reads the key from there and never asks you to paste it into the conversation.

## Contents

- Skill `graphops-subgraphs`, published at https://docs.graphops.xyz/.well-known/agent-skills/graphops-subgraphs/SKILL.md
- MCP server `graphops-subgraphs` at `https://subgraphs.graphops.xyz/v1/mcp`
- Requires the `graphops` plugin

The skills contain instructions and links to the live documentation, never scripts. They are generated from the GraphOps documentation; see https://docs.graphops.xyz/ai-agents for other ways to use GraphOps with AI agents.
