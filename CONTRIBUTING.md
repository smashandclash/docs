# Contributing to the developer docs

Start with the [content map](README.md#find-the-right-source). Public documentation is MDX; `README.md`, `AGENTS.md` and this file explain how to maintain it.

## Verify a change

Use the game repository as the source of truth:

| Contract | Source in `hktitan/snc-fable` |
| --- | --- |
| SDK methods, options and return types | `packages/sdk/src/index.ts` and `packages/sdk/package.json` |
| CLI commands, JSON output, state and exit codes | `packages/cli/src/cli.ts`, `store.ts`, `errors.ts` |
| HTTP routes and authorization | `api/_lib/gamesRoutes.ts`, `api/_lib/games.ts` |
| Executable SDK and CLI behavior | `tests/sdk.test.ts`, `tests/cli.test.ts`, `tests/watch-feed.test.ts` |
| Card identity and values | `src/engine/cards.ts` |

Check optional fields, incomplete waits, draws, abandoned games and invite-token rotation. A method name such as `waitForEnd` is not evidence that the method always returns a finished result. Read its implementation and tests.

Use complete imports and initialized values in runnable examples. Clearly identify excerpts and replace secrets with placeholders. Quote shell URLs containing `&`. Keep current instructions focused on the supported SDK version; release history belongs in `changelog.mdx`.

## Preview and validate

```bash
npx mint dev
npx mint broken-links
npx mint validate
```

The preview defaults to `http://localhost:3000`. Check changed pages, navigation and code blocks. CI additionally verifies that every page named in `docs.json` exists. Run `git diff --check` before review.

In a Windows checkout whose path includes `&`, npm command shims can fail. Invoke the installed Mintlify JavaScript entry point directly with Node when needed (`node <path-to-mint>/index.js broken-links`). In the game checkout, use its local Node entry points for TypeScript and Vitest instead of npm script shims.

Mintlify's generated API pages can also fail on Windows when an OpenAPI operation title produces a filename containing `?`. If validation reports that generated filename error, validate the full API build on Linux; do not change the game's API solely to work around a local filename restriction. Navigation, MDX compilation, example type checks and link checks remain useful local checks.

For contract changes, type-check representative examples against the matching SDK source and run the existing SDK/CLI tests in the game repository. Validation should use in-memory routes or a development server; avoid creating public games simply to test documentation.

## Publish

The origin is `https://github.com/smashandclash/docs.git`. Mintlify's GitHub app deploys `main` to `https://docs.smashandclash.in`. Verify the remote and diff, publish the reviewed docs commit, and check CI and the affected public pages. Publishing this repository does not require a game deployment or a package release.

The API reference is loaded from the game's public OpenAPI document. Mintlify's generated `llms.txt` and `llms-full.txt` follow the published MDX source. Treat those as generated outputs, and verify them after a public docs release.
