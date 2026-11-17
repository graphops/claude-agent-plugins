# GraphOps plugins for Claude

Claude Code plugins for GraphOps blockchain data services. They give Claude the instructions to use GraphOps RPC, Subgraphs and Substreams correctly, MCP servers to query them, and the GraphOps CLI workflow to manage Managed Subgraphs.

## Install

```text
/plugin marketplace add graphops/claude-agent-plugins
```

Then install the plugins your project needs, for example:

```text
/plugin install graphops-rpc@graphops
```

## Plugins

| Plugin | What it does |
| --- | --- |
| [`graphops`](plugins/graphops) | Choose between GraphOps RPC, Subgraphs and Substreams, handle GraphOps API keys and error codes, and search the GraphOps documentation through its MCP server. |
| [`graphops-rpc`](plugins/graphops-rpc) | Read EVM and Bitcoin chain data with GraphOps RPC: query blocks, balances, contract calls and event logs through the RPC MCP server, and write bounded, recoverable JSON-RPC code. |
| [`graphops-subgraphs`](plugins/graphops-subgraphs) | Query indexed blockchain entities with GraphOps Subgraphs: read schemas, freshness and query results through the Subgraphs MCP server, and write paginated GraphQL code. |
| [`graphops-substreams`](plugins/graphops-substreams) | Stream ordered blockchain data with GraphOps Substreams: run packages, backfill block ranges and build sinks that resume from cursors and handle reorgs. |
| [`graphops-platform`](plugins/graphops-platform) | Deploy, stage, promote and check Managed Subgraphs and create Substreams keys with the GraphOps CLI, signed in as you and approved in your browser. |

## About this repository

Every file here is generated from the GraphOps documentation each time it is deployed, so the skills match https://docs.graphops.xyz exactly. Changes made here directly are overwritten. To report a problem or suggest a change, contact GraphOps at https://graphops.xyz/contact/.
