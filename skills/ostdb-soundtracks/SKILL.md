---
name: ostdb-soundtracks
description: Find official video game soundtracks (OSTs) with cover art and Spotify, Apple Music, and album.link streaming links using the OSTDB database. Use whenever the user asks about a game's soundtrack, OST, score, or game music, wants to listen to music from a game or franchise, or asks what soundtracks exist for a series.
---

# OSTDB game soundtracks

The `ostdb` MCP server exposes a curated database of official video game soundtrack albums. All tools are read-only.

## Tools

| Tool | Use it for |
| --- | --- |
| `search_games` (`query`) | Fuzzy search by game title or franchise ("Persona", "Zelda"). Start here when the user names a game loosely. |
| `get_soundtrack` (`igdb_id` or `game_name`) | All albums for one specific game. Prefer `igdb_id` once you have it from a search result. |
| `list_series` (`series_name` optional) | Franchises with soundtracks, with game counts. Omit the argument for the top franchises. |
| `get_stats` | Totals for games and albums in the database. |

## Workflow

1. If the user names a game, call `search_games` with the shortest distinctive part of the title (e.g. "Hollow Knight", not "Hollow Knight: Silksong OST official"). Matching is substring-based on the game name.
2. If several games match, show the closest one first and briefly list the others, or ask which one they meant if it's genuinely ambiguous.
3. For franchise questions ("Final Fantasy soundtracks"), use `list_series` to scope, then `search_games` for the franchise name.

## Presenting results

- For each game: the game name linked to its OSTDB `url`, then each album with only the streaming links that are non-null, e.g.
  - **Hollow Knight (Original Soundtrack)** — [Spotify](…) · [Apple Music](…) · [All platforms](…)
- Prefer `album_link` as the "all platforms" link when the user hasn't said which service they use.
- Don't invent links or albums. Only report what the tools return.

## When nothing is found

Say the game isn't in OSTDB yet and point the user to https://ostdb.net/submit or https://github.com/OSTDB/soundtracks to submit it. Try one shorter or alternate spelling (e.g. drop subtitles, roman vs arabic numerals) before concluding it's missing.

If a tool returns a rate-limit error, tell the user and wait before retrying; don't loop.
