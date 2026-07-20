# Changelog

## 0.1.4

- Update

## 0.1.3

- Fixed broken YAML frontmatter in the collection-insights and pull-list-planner skills. A stray colon in the `description` line kept those two skills from loading their metadata, so Claude couldn't pick them up on its own. Both work now.
- Moved `.mcp.json` to the standard `{ "mcpServers": { ... } }` shape and dropped the redundant `mcpServers` path from the manifest — the file is auto-discovered at the plugin root.
- Added a `$schema` reference to `plugin.json` for editor validation.
- Rounded out the keyword list (manga, pull-list, market-prices).

## 0.1.2

- Earlier release.
