---
description: Plans the user's VerseDB pull list: upcoming releases for series they follow, catching up on what shipped, finding new ongoings worth adding, and keeping the list current. Use when the user asks "what's coming out", "what's on my pull list", "new this week", "what should I add to my pulls", or "am I caught up".
---

# Pull-list planner

Keep the user current on the ongoing series they follow. The whole VerseDB MCP is Pro-only, so on an auth/subscription error (`pro_required` / HTTP 402), tell the user it needs Pro and stop.

## Where they stand

- `get-my-pull-list-tool` lists the series they follow.
- `get-upcoming-releases-tool` shows what's shipping soon. Intersect it with the pull list to build "coming up for you".
- `get-series-progress-tool`, run per followed series, flags where they've fallen behind (issues out but unread).

## What to surface

1. **What's coming.** Upcoming issues for followed series, by date. Group by week, and note key issues (`get-key-issue-reasons-tool`) and finales.
2. **Catch up.** Followed series with shipped-but-unread issues. Offer to mark caught-up issues read (`mark-as-read-tool`) once the user confirms they've read them. Never mark read on your own.
3. **What to add.** Suggest new ongoings via `get-trending-tool` and `search-series-tool`, filtered to series they don't already follow and matched to the creators and genres in their current pulls. Add with `add-to-pull-list-tool` after confirmation. Prune dead or ended series with `remove-from-pull-list-tool`.

## Present it

Lead with "Coming up" (dated), then "Catch up" (behind count per series), then "Consider adding". List dates, series, and issue numbers. Confirm before any add, remove, or mark-read, and report what changed.
