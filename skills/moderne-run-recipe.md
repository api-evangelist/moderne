---
name: run-recipe
description: Discover, configure, and run an OpenRewrite recipe across a Moderne organization, then interpret the results.
api: mcp/moderne-mcp.yml
source: https://docs.moderne.io/user-documentation/agent-tools/skills
method: searched
tools: [searchForRecipe, describeRecipeOptions, describeRecipeDataTables, runRecipe, processDataTableSql]
operations: [runRecipe, recipeRun]
---

# Run a Moderne recipe against an organization

First-party Moderne skill (installed via `mod config agent-tools install`). Runs a
recipe at organization scale using the hosted Moderne MCP server or the GraphQL API.

## Auth
Use a Moderne personal access token: `Authorization: Bearer <token>` plus
`X-Moderne-Platform-Version: v2`. Same token for the GraphQL API and remote MCP
server. See `authentication/moderne-authentication.yml`.

## Steps
1. `searchForRecipe` — find a recipe by natural-language query for the organization.
2. `describeRecipeOptions` — inspect the recipe's configurable options.
3. `describeRecipeDataTables` — inspect the data tables it will produce.
4. `runRecipe` — run against a specific `organizationId` (never the root `ALL`).
   Via GraphQL: mutation `runRecipe(run: RecipeRunInput!)` returns a run `id`.
5. Poll `recipeRun(id)` for `state` (~3s interval) until completion.
6. `processDataTableSql` — query the resulting data tables (DuckDB SQL) by run id.

## Conventions & errors
- Async: runRecipe returns an id; poll recipeRun for state. No idempotency key.
- Errors surface in the GraphQL `errors[]` array; 401 on missing/invalid token.
- See `conventions/moderne-conventions.yml`.
