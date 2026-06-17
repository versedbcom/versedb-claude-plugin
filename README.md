# VerseDB plugin for Claude Code

Search, catalog, and discover comics through the [VerseDB](https://versedb.com) MCP. The plugin bundles the connection along with a few skills and an agent that know how to use the tools.

VerseDB is a comic database covering comics, manga, manhwa, manhua, and bande dessinée. The MCP gives you around 50 tools. Most of them search and fetch data: titles, series, issues, creators, characters, publishers, teams, story arcs, universes, events, tier lists, comic shops, and podcasts. The rest are personal: your collection, pull lists, reading progress, lists, reviews, and market prices.

## What you get

The MCP itself connects at `https://versedb.com/mcp/api`. Installing the plugin wires it up, and Claude Code handles the OAuth flow the first time you use it.

### Agents

- `comic-concierge` is the general-purpose helper. It understands how Titles, Series, and Issues relate, searches before it fetches, and asks before writing anything to your account.
- `comic-researcher` is read-only and meant for bigger questions that touch a lot of entities, like tracing a character across eras, mapping out a crossover, or surveying a creator's influence. It comes back with a written report and its sources.

### Skills

- `reading-order` works out the chronological order for a character, arc, event, creator run, or series.
- `collection-insights` looks at collection value, gaps in your runs, reading progress, and the key issues you own.
- `discover-comics` pulls recommendations from trending titles, tier lists, key issues, and reviews.
- `pull-list-planner` handles upcoming releases, catching up, and tidying your pull list.
- `quick-catalog` bulk-adds comics to your collection from a pasted list or a series plus a range.
- `character-dossier` builds a character profile: first appearance, key issues, affiliations, and where to start.
- `creator-spotlight` covers a creator's work by role, their signature runs, and what to read first.

## Requirements

You'll need a VerseDB [Pro subscription](https://versedb.com/subscription). The hosted MCP requires Pro for **every** tool — search and browse included, not just the personal ones. Without it, calls come back with a `pro_required` / HTTP 402 error.

## Install

```text
/plugin marketplace add versedbcom/versedb-claude-plugin
/plugin install versedb@versedb
```

To test a local checkout instead:

```text
claude --plugin-dir /path/to/versedb-claude-plugin
```

## Usage

Just ask for what you want in plain language: "what order do I read Saga in", "what's my collection worth", "what's coming out for my pull list", "recommend something like Immortal Hulk". The concierge and the skills figure out which tools to call.
</content>
</invoke>
