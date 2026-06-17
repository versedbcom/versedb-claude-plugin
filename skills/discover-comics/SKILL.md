---
description: Recommends comics to read or buy from VerseDB, drawing on trending titles, community tier lists, key issues, and well-reviewed books, tuned to a genre, character, creator, or the user's tastes, and can save the picks to a list. Use when the user asks "what should I read", "what's popular", "recommend something like X", "what's hot right now", or "find me good X comics".
---

# Discover comics

Recommend reading worth the user's time, and back every pick with a reason.

The VerseDB MCP is Pro-only, every tool including search. If a call returns an auth/subscription error (`pro_required` / HTTP 402), tell the user it needs Pro and stop.

## Gather signal

Pull from several sources and balance them; don't lean on one. Start with `get-trending-tool` for what's currently popular. For curated rankings in a niche, run `search-tier-lists-tool` then `get-tier-list-tool`. Weight candidates by community rating with `get-community-reviews-tool` (1–5 stars). To surface historically significant books, pair `get-key-issue-reasons-tool` with `search-issues-tool`. When the user anchors on a creator, character, or publisher ("more like Saga", "anything by Tom King"), go straight to the matching `search-*` tool.

Walk pagination (default 50) on any list you pull before ranking; a truncated set skews the picks.

## Tune to the user

- If they name a reference point ("like X"), resolve X first (`search-series-tool` / `get-series-tool`) and match on creators, genre, publisher, and tone.
- If they have a collection or lists, read `get-my-collection-tool` / `get-my-lists-tool` to avoid recommending what they already own and to infer taste.
- Respect stated constraints: medium (comic/manga/manhwa/etc.), all-ages vs. mature, ongoing vs. complete, single issues vs. collected editions.

## Present it

A short ranked list, 5–8 picks rather than a dump. Write each as `Series (year), one-line why (the signal behind it)`. Group them loosely: a few safe bets, then a couple of wilder swings. Say where to start, tying in the `reading-order` skill for anything with a complex entry point. If you quote a value, state the grade; prices are grade-dependent.

End by offering to save picks to a list (`create-list-tool` + `add-to-list-tool`) or add to their pull list or collection. Confirm before writing.
