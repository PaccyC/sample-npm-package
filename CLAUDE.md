# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Package

`@PaccyC/sample-package` — a minimal npm package published to the npm registry. The entry point is `index.js`, which exports a `Greetings` class with static methods.

## Commands

```bash
# Release a new version (bumps version, updates CHANGELOG, pushes tags, publishes to npm)
npm run release
```

No build step or test runner is configured. `npm test` exits with an error by default.

## Release workflow

Releases are managed with [`standard-version`](https://github.com/conventional-changelog/standard-version). It reads conventional commit messages to determine the version bump and auto-generates `CHANGELOG.md` entries. The release script runs `standard-version`, then `git push --follow-tags`, then `npm publish` in sequence.

Use [Conventional Commits](https://www.conventionalcommits.org/) for all commit messages (`feat:`, `fix:`, `chore:`, etc.) so that `standard-version` can correctly classify changes.

## Known issue

`package.json` declares `"type": "commonjs"` but `index.js` uses ES module `export` syntax. If consumers encounter import issues, the fix is either to change `"type"` to `"module"` in `package.json`, or to convert `index.js` to `module.exports`.
