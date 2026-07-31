---
name: create-recipe
description: Author a new OpenRewrite recipe (declarative, Refaster, or imperative) using correct Moderne patterns.
api: mcp/moderne-mcp.yml
source: https://docs.moderne.io/user-documentation/agent-tools/skills
method: searched
tools: [learn_recipe, pattern_replace]
---

# Create an OpenRewrite recipe

First-party Moderne skill (installed via `mod config agent-tools install`). Teaches an
agent to author recipes following OpenRewrite conventions.

## Steps
1. Choose the recipe type:
   - Declarative YAML — compose existing recipes.
   - Refaster template — simple `@BeforeTemplate`/`@AfterTemplate` expression swaps
     (runnable via the `pattern_replace` MCP tool).
   - Imperative Java — complex visitor logic.
2. Apply critical patterns: LST immutability, visitor traversal, type matching with
   `MethodMatcher`, and proper import handling.
3. Write tests with the `RewriteTest` framework (before/after and no-change cases).
4. Emit data tables for downstream analysis.

## Notes
- Use `learn_recipe` to inspect an existing recipe's options and data-table schemas.
- Do not use for running/debugging (use `run-recipe`) or unrelated Java programming.
