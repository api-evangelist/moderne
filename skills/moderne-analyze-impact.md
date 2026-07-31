---
name: analyze-impact
description: Turn Moderne recipe-run data tables into executive reports and visualizations.
api: mcp/moderne-mcp.yml
source: https://docs.moderne.io/user-documentation/agent-tools/skills
method: searched
tools: [query_datatable, processDataTableSql]
---

# Analyze recipe impact

First-party Moderne skill (installed via `mod config agent-tools install`). Turns the
data tables produced by a recipe run into reports and visualizations.

## Steps
1. Identify the recipe run and the data tables it produced
   (`describeRecipeDataTables`).
2. Query the results with SQL — `query_datatable` (local MCP, DuckDB) or
   `processDataTableSql` (remote MCP, by run id).
3. Summarize which repositories changed the most, quantify the migration/remediation,
   and produce executive-ready reports and visualizations.

## Notes
- Data tables can also be downloaded and analyzed with the Moderne BI templates
  (Athena, Snowflake, BigQuery, Databricks, DuckDB).
- See `conventions/moderne-conventions.yml` for the async run + poll flow.
