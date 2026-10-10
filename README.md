# OSTDB plugin for Claude

Search [OSTDB](https://ostdb.net) for official video game soundtracks, with cover art and Spotify, Apple Music, and album.link links.

## What's included

- **MCP server** `ostdb` → `https://mcp.ostdb.net/mcp` (tools: `search_games`, `get_soundtrack`, `list_series`, `get_stats`)
- **Skill** `ostdb-soundtracks` so Claude uses the tools automatically when you ask about game music
- **Command** `/ostdb:soundtrack <game>`

## Install (Claude Code)

From GitHub (once this folder is pushed to a repo):

```
/plugin marketplace add OSTDB/Claude_Plugin
/plugin install ostdb@ostdb
```

Locally while developing:

```
/plugin marketplace add /path/to/ostdb_claude_plugin
/plugin install ostdb@ostdb
```

## Use without the plugin

The MCP server works on its own too:

```
claude mcp add --transport http ostdb https://mcp.ostdb.net/mcp
```

In claude.ai, add `https://mcp.ostdb.net/mcp` as a custom connector.

## Examples

- "What's the soundtrack for Hollow Knight?"
- "Give me Spotify links for every Persona OST"
- `/ostdb:soundtrack Celeste`
