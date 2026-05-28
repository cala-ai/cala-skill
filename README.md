# Cala Skill

Cala pre-processes the world's public information and serves it as structured data for AI agents. Instead of scraping web pages, your agent queries Cala and gets back typed, sourced JSON — for any real-world entity.

## What Cala covers

- **Organizations** — companies, startups, investment firms, educational institutions, stock exchanges. Query by sector, location, funding stage, employee count, revenue, or any combination. Traverse ownership chains, subsidiaries, and parent companies.
- **People** — founders, executives (CEO, CTO, COO), board members, investors. Find who runs a company, who sits on a board, or which people have moved between organizations.
- **Funding & investment** — funding rounds by series, amount, date, and investor. Portfolio lookups for VC and PE firms. Investor co-investment patterns.
- **M&A & corporate events** — acquisitions, mergers, divestitures, SEC filings, and other corporate actions with sourced dates.
- **Industries & markets** — sector-level data, competitive landscapes, and cross-industry relationships.
- **Laws & regulations** — legislation and regulatory frameworks (GDPR, EU AI Act, etc.) with scope, definitions, and requirements.
- **Countries & regions** — geopolitical entities, economic profiles, sovereign funds, and country-level relationships.
- **Products** — named products, their makers, launch dates, and entity relationships.
- **Events & awards** — conferences, summits, industry awards, and their participants or recipients.

All responses include sources with URLs and data freshness dates.

## Prerequisites

You need a Cala API key to use this skill: https://console.cala.ai/api-keys

## Installing the skill

The skill file (`SKILL.md`) gives your agent the knowledge it needs to query Cala effectively — what tools exist, how to use them, and how to handle edge cases.

```bash
npx skills add cala-ai/cala-skill
```

This installs the skill for Claude Code, Cursor, Copilot, Amp, Codex, and more in one step.

## Connecting to Cala

The skill alone gives your agent the instructions — pairing it with a live Cala connection lets your agent actually execute queries in real time. This combination is the recommended setup.

**MCP (recommended):**

For clients with native HTTP MCP support (Cursor, VS Code):

```json
{
  "mcpServers": {
    "Cala": {
      "url": "https://api.cala.ai/mcp/",
      "headers": {
        "X-API-KEY": "YOUR_CALA_API_KEY"
      }
    }
  }
}
```

For Claude Desktop and other clients:

```json
{
  "mcpServers": {
    "Cala": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://api.cala.ai/mcp/",
        "--header",
        "X-API-KEY: YOUR_CALA_API_KEY"
      ]
    }
  }
}
```

Full setup guide: https://docs.cala.ai/integrations/mcp

**REST API:**

Base URL: `https://api.cala.ai/v1`  
Auth header: `X-API-KEY: <your-key>`  
Full spec: https://api.cala.ai/openapi.json

## Tools

Once connected, your agent has access to five tools:

| Tool | Use |
|------|-----|
| `knowledge_query` | Filter and list entities by criteria |
| `knowledge_search` | Open-ended questions with cited answers |
| `entity_search` | Fuzzy name → UUID lookup |
| `retrieve_entity` | UUID → full structured profile |
| `entity_introspection` | Discover available fields for an entity |

## Links

- Homepage: https://cala.ai
- Docs: https://docs.cala.ai
- MCP setup: https://docs.cala.ai/integrations/mcp
- API console: https://console.cala.ai
