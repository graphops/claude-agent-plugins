# GraphOps Platform

Deploy, stage, promote and check Managed Subgraphs and create Substreams keys with the GraphOps CLI, signed in as you and approved in your browser.

## Install

```text
/plugin marketplace add graphops/claude-agent-plugins
/plugin install graphops-platform@graphops
```

## Set up

This plugin drives the `graphops` CLI, so it needs a shell and works in Claude Code. Install the CLI yourself first; the plugin never installs software.

The first time a task needs the platform, Claude runs `graphops auth login` and shows you a sign-in address and code. Approve it in your browser. The CLI then acts as you, with your role in each organization, and the platform records every change under your account. Claude asks before any command that deploys, promotes, creates a key or spends credits.

## Contents

- Skill `graphops-cli`, published at https://docs.graphops.xyz/.well-known/agent-skills/graphops-cli/SKILL.md
- Requires the `graphops` plugin

The skills contain instructions and links to the live documentation, never scripts. They are generated from the GraphOps documentation; see https://docs.graphops.xyz/ai-agents for other ways to use GraphOps with AI agents.
