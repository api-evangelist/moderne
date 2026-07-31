---
name: create-organization
description: Build a working set of repositories (an organization) to run Moderne recipes against.
api: mcp/moderne-mcp.yml
source: https://docs.moderne.io/user-documentation/agent-tools/skills
method: searched
tools: [searchForRecipe]
operations: [mod git sync csv]
---

# Create a Moderne organization (working set of repositories)

First-party Moderne skill (installed via `mod config agent-tools install`). Helps an
agent assemble a custom set of repositories to test and run recipes against.

## Steps
1. Find repositories by language or technology (Spring Boot, JPA, Kafka, …), or list
   all accessible repos — across GitHub, GitLab, Bitbucket, Sourcegraph, Libraries.io.
2. Generate a `repos.csv` with the correct format and organizational hierarchy.
3. Sync repositories with `mod git sync csv`.
4. Organize repositories by team, technology, or business domain for focused testing.

## Notes
- Organizations are identified by id, path (e.g. `ALL/Default`), or name; query the
  `organizations` field of the GraphQL API to discover them.
- See `data-model/moderne-data-model.yml` (Organization ⇄ Repository).
