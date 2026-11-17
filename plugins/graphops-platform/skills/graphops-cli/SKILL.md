---
name: graphops-cli
description: Manage GraphOps platform resources with the graphops CLI under the person's own sign-in. Deploy, stage, promote and check Managed Subgraphs from a graph-cli project, list and select organizations, and create or store a Substreams API key. Use when a task changes or inspects what an organization runs on GraphOps rather than reading chain data.
metadata:
  version: 74ad4379ba53817b
  source: https://docs.graphops.xyz/.well-known/agent-skills/graphops-cli/SKILL.md
---

# GraphOps CLI

The `graphops` CLI acts on the GraphOps platform as the person who signed it in, with that
person's role in each organization. Every change it makes is recorded under their account. Use it
for platform actions; read chain data with the `graphops-rpc`, `graphops-subgraphs` and
`graphops-substreams` skills.

## Before the first command

- Check that `graphops` is on the `PATH`. If it isn't, tell the person that the GraphOps CLI is
  needed for this task and stop. Never install it or any other software yourself.
- Run `graphops --json doctor` to check the configuration, the session and the tools the CLI wraps,
  such as `graph` for Subgraph deploys.
- Run `graphops --json auth status`. If no one is signed in, run `graphops auth login`, show the
  person the address and code it prints, and wait for them to approve it in the browser. Never
  use `auth login --with-token`. See [Sign in to the CLI](https://docs.graphops.xyz/platform/cli-sign-in.md).
- Run `graphops --json orgs list`, and pass the organization explicitly with
  `--organization <slug>` on every later command instead of relying on the stored selection.

## Rules for every command

- Pass `--json`, read the single JSON document on stdout, and act on the exit code, not on the
  wording of messages on stderr.
- Ask the person before any command that changes what customers are served or what is spent:
  `subgraphs deploy`, `subgraphs create`, `subgraphs promote`, `subgraphs unstage`,
  `substreams key create`, and Substreams runs beyond a small block range. Say what the command
  will do, including that indexing a Managed Subgraph is billed from creation.
- Never run `auth token`, `substreams env` or `substreams key show --reveal`, and never put a
  credential in a file, a message or a command line. The CLI keeps credentials in the operating
  system's credential store.
- Stop on exit codes 3 and 5 instead of retrying. Don't loop on `wait`; one `wait` with a timeout
  is the whole check.

| Exit code    | Meaning                                                              | What to do                                                                                                                |
| ------------ | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `0`          | Success                                                              | Continue.                                                                                                                 |
| `2`          | Usage error or unsupported network                                   | Fix the arguments. Run the command with `--help` if unsure.                                                               |
| `3`          | Not signed in, session expired, or the change needs a recent sign-in | Run `graphops auth login` with the person, then run the command again once.                                               |
| `4`          | No Substreams key stored                                             | Ask whether to create one with `substreams key create`.                                                                   |
| `5`          | The platform refused the operation                                   | Read `error.code` and its entry in [Error reference](https://docs.graphops.xyz/platform/errors.md), then tell the person. |
| `6`          | `wait` timed out                                                     | Report the last status. Don't start another wait without asking.                                                          |
| `1` or `127` | Network failure, unexpected answer, or a wrapped tool is missing     | Report the error to the person.                                                                                           |

## Deploy and release a Managed Subgraph

The person's graph-cli project builds as usual with `graph codegen` and `graph build`; run those
directly. Then:

1. `graphops --json --organization <slug> subgraphs list` shows the organization's Managed
   Subgraphs. Use a name from it, or agree a new one with the person.
2. `graphops --json --organization <slug> subgraphs deploy <name> -- <graph deploy arguments>`
   uploads the build and stages it as the Next version of that Managed Subgraph. Add `--create`
   only when the person agreed to create a new one. Add `--accept-schema-changes` only when they
   agreed that queries using removed or changed fields will break, and `--replace-next` only when
   they agreed to discard another staged version.
3. `graphops --json --organization <slug> subgraphs wait <name> --for promotable --timeout 30m`
   waits until the Next version can be promoted. Use `--for synced` for a new Managed Subgraph.
4. `graphops --json --organization <slug> subgraphs status <name>` shows the current and Next
   versions. Report both to the person.
5. With their agreement, `subgraphs promote <name>` makes the Next version current, and
   `subgraphs unstage <name>` cancels it instead.

To serve a Deployment CID or Graph Network Subgraph that already exists, use
`subgraphs create <name> --cid <CID>` or `subgraphs create <name> --subgraph-id <ID>`.

Read [Managed Subgraphs](https://docs.graphops.xyz/subgraphs/managed-subgraphs.md) for how versions, staging and billing work,
and [Develop and release](https://docs.graphops.xyz/subgraphs/guides/develop-and-release.md) for the release flow.

## Substreams with the stored key

- `graphops --json --organization <slug> substreams key show` says whether a key is stored, by ID
  and last four characters.
- With the person's agreement, `substreams key create --name <label>` creates a key and stores it
  without printing it. Use a label that says an agent's environment holds it.
- `substreams run`, `substreams gui` and `substreams sink noop|protojson|webhook` run the
  `substreams` tool with the GraphOps endpoint and the stored key. Pass the network and every
  `substreams` argument unchanged after the command.
- `substreams endpoint --network <name>` prints a network's endpoint.

## What the CLI doesn't do

Endpoint Aliases, organization members, billing and deleting resources aren't CLI commands. Tell
the person to make those changes in the GraphOps platform.

## Keep these instructions current

These instructions are published at https://docs.graphops.xyz/.well-known/agent-skills/graphops-cli/SKILL.md. At the start of a task, fetch that URL and compare
its `metadata.version` with the version of this copy. When they differ, tell the person that
their GraphOps skills are out of date, and follow the published version for the task.
