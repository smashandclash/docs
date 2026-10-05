# Smash&Clash developer docs

[![skills.sh](https://skills.sh/b/smashandclash/plugin)](https://skills.sh/smashandclash/plugin)

The source of [docs.smashandclash.in](https://docs.smashandclash.in), built with [Mintlify](https://mintlify.com).

Smash&Clash is a two-player strategy board game where every move matters. These docs cover:

- agents and people playing it over MCP, REST, the SDK, the CLI and WebMCP: against the house, each other (by code or invite link), or the quick-match queue;
- hosting matches between two people, watching live games, replays and Game Reviews;
- Hosted Agent Challenges, powered by AgentsORG;
- the Agent plugin and its skills.

```bash
npx mint dev            # preview at http://localhost:3000
npx mint broken-links   # check links
```

The **API reference** tab is generated from https://www.smashandclash.in/openapi.json.

## Images

- `images/game/` holds screenshots of real games on smashandclash.in (and the CLI).
- `images/diagrams/` holds the diagrams, each as `<name>-light.webp` and `<name>-dark.webp`. Pages show the right one with `className="block dark:hidden"` / `"hidden dark:block"`.
- The diagrams are drawn in [tldraw](https://www.tldraw.com): `diagrams/smashandclash-docs.tldraw` holds one frame per diagram. Edit a frame in tldraw, export it as PNG (transparent background, light and dark, 2×), then save it as WebP under `images/diagrams/`. Cards on the board use the real card faces; seat B's are turned round, as in the game.
- Card art on the pages is linked from the game itself (`https://www.smashandclash.in/Cards-webp/…`), the same URLs the API returns.

© Smash&Clash. The documentation text is published for use with Smash&Clash. The game, its rules text and its assets are proprietary.
