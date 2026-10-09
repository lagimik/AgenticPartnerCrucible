# Postgres MCP Server: Connect AI coding agents to PostgreSQL

**Source:** https://techcommunity.microsoft.com/blog/adforpostgresql/postgres-mcp-server-connect-ai-coding-agents-to-postgresql/4561273
**Captured:** 2026-10-03
**Published:** 2026-10-01 (Microsoft Blog for PostgreSQL / Microsoft Community Hub)
**Author:** Aditi_Gupta

---

## Announcement

Microsoft has open-sourced the **Postgres MCP Server** under the MIT
License. It is built entirely in Rust for fast, resource-efficient
operation and connects Model Context Protocol (MCP)-compatible coding
agents to PostgreSQL so an agent can inspect real database context and run
permitted operations.

- Works with PostgreSQL running locally, on-premises, on Azure, AWS, GCP, or
  through another PostgreSQL-compatible service — not Azure-exclusive.
- Audience: application developers, database administrators, data
  professionals, platform engineers, and PostgreSQL enthusiasts using a
  coding agent.

## What the exposed tools let an agent do

After connecting to a profile, a coding agent can be asked things like
"List the tables in my PostgreSQL database," "Show me the ten most recent
orders," "Generate the schema for these tables and indexes," or "What is
slowing down my PostgreSQL server?" The underlying tools let the agent:

- **Generate queries and run analytics** — run read-only SQL, or use
  separate tools for data vs. schema changes.
- **Explore and design schemas** — inspect tables, indexes, functions,
  sequences, and other database objects before generating changes.
- **Diagnose performance** — detect server capabilities and collect focused
  performance metrics for the server and its queries.
- **Manage connections** — create named connection profiles, connect to the
  right database, and switch environments without placing credentials in
  the MCP client configuration.

## Install and connect

Prerequisites: Node.js 22+ (includes npm/npx); Linux x64/arm64, macOS
x64/arm64, or Windows x64 (Windows on Arm uses x64 emulation); an
MCP-compatible coding agent/client; a reachable PostgreSQL (or
wire-compatible) database and a role with the permissions needed for the
intended tasks.

`npx` runs the package with no separate install; a global install is
available via `npm install --global @microsoft/postgres-mcp`. A profile is
created with `postgres-mcp connection add <name> "<connection-string>"`,
and its password is stored separately via
`postgres-mcp connection set-password <name>` — the password is kept in the
OS keyring, not in the profile. Headless/CI environments without a keyring
use an environment-based connection option instead.

MCP client config example:
```json
{ "mcpServers": { "postgres": { "command": "npx", "args": ["-y", "@microsoft/postgres-mcp", "run"] } } }
```
Configuration format/location differs by client; the Postgres MCP usage
guide documents supported clients.

For Azure Database for PostgreSQL, the server can use Microsoft Entra ID
when a saved profile has no password.

## Security boundary

PostgreSQL role permissions remain the actual security boundary. New
profiles permit write tools by default unless `access_mode: ro` is set; for
exploration, pair that setting with a read-only database role. The MCP
client controls approval prompts, and CSV tools can read only from approved
local paths.

## Complementary Postgres Skills

The open-source **Postgres Skills** repository complements the MCP server
with expert guidance for query performance, indexing, vector search,
security, operations, Azure workflows, and AI/knowledge-graph scenarios.
These reusable instructions help a coding agent apply PostgreSQL best
practices while investigating an issue or completing a task — the MCP
server supplies live database context and permitted operations; the skills
supply the expert judgment for how to use them.

## Next steps named in the source

- Postgres MCP Server repository
- Postgres MCP usage and security guide
- Postgres Skills plugin setup guide
- Postgres MCP GitHub issues (feedback/contribution)
