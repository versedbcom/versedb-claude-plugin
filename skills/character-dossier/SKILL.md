---
description: Builds a profile of a comic character using VerseDB, covering first appearance and key issues, teams and affiliations, the story arcs and events they anchor, and where to start reading. Use when the user asks "tell me about X", "who is X", "X's first appearance", "X's key issues", or "where do I start with X".
---

# Character dossier

Give a reader or collector a sourced profile they can use: who the character is, which issues matter, and where to start reading.

The VerseDB MCP is Pro-only, every tool including search. If a call returns an auth/subscription error (`pro_required` / HTTP 402), tell the user it needs Pro and stop.

## Resolve the character

`search-characters-tool` first. Common names collide across publishers and legacies (think of all the Robins, or the various Captain Marvels). When several strong matches come back, show them with publisher/universe and let the user pick. Then `get-character-tool` for the core record.

## Build the dossier

Gather each piece from its own source:

- **First appearance & key issues.** Surface the debut and other significant books, labeled with their significance via `get-key-issue-reasons-tool` (1st appearance, origin, death, first cover, and so on).
- **Affiliations.** Teams they belong to (`search-teams-tool` / `get-team-tool`) and the universe they live in (`get-universe-tool`).
- **Defining stories.** The story arcs and events they anchor (`search-story-arcs-tool`, `search-events-tool`, `get-event-tool`).
- **Notable runs.** The series where they're central (`search-series-tool`), plus the creators most associated with them.

## Present it

Structure it so it scans:
1. **Who.** One-paragraph identity: publisher, universe, alter ego, debut year.
2. **Key issues.** Bulleted, each with its significance and issue id, ordered by importance (1st appearance first). Flag which are expensive, cross-referencing `get-market-prices-tool` only if the user cares about value.
3. **Affiliations.** Teams and universe.
4. **Defining stories.** Arcs and events, in suggested reading order.
5. **Where to start.** One concrete entry point: a series plus issue, or a collected edition. Hand off to the `reading-order` skill for anything complex.

End by offering to save the key issues as a want-list, add them to the user's collection, or build a reading list.
