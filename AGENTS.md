# Working on Smash&Clash developer docs

This is the Mintlify source for `docs.smashandclash.in`, separate from the shipping game. Read the repository's `README.md` for the content map and `CONTRIBUTING.md` for validation and publication.

- Verify SDK behavior in `packages/sdk/src/index.ts` and CLI behavior in `packages/cli/src/cli.ts` of the `hktitan/snc-fable` repository. Check package versions before calling a feature current. Local sibling checkout: `../fable` when available.
- Document what is implemented. Separate SDK HTTP gameplay, the website's offline engine, MCP tools, browser WebMCP and host-specific plugin UI. Do not imply that one surface exports the others.
- Keep seat tokens and invite URLs out of committed examples and logs. Use explicit placeholders. Describe invite games as unlisted, because the game ID still permits public-board reads.
- Examples must use legal moves from the current view, handle draws and incomplete waits, and distinguish `GameState` from `SeatSync`. Link to `reference/sdk-lifecycle.mdx` instead of copying its complete contract.
- Update `docs.json` for new public pages. Preserve existing public routes and anchors when revising content. Keep historical versions in `changelog.mdx`; remove obsolete workarounds from current instructions.
- Do not change the game's renderer, production configuration, assets or API to make an example fit. Resolve documentation discrepancies from source and report implementation issues separately.
- Check the working tree before editing and preserve other contributors' changes. Publishing `main` triggers the docs deployment; use the destination and authorization established for the current task.
