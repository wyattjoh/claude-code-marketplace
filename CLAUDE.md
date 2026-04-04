# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A Claude Code plugin marketplace registry. The core artifact is `.claude-plugin/marketplace.json`, which lists available plugins with their metadata and source repositories. There is no application code to build, lint, or test.

## Key Files

- `.claude-plugin/marketplace.json` - The marketplace manifest. Each entry in the `plugins` array defines a plugin's name, version, description, source repo, and optional git ref.
- `release-please-config.json` / `.release-please-manifest.json` - Automated versioning via release-please (simple release type, no component prefix in tags).
- `.github/workflows/release.yml` - On push to main, runs release-please and creates floating `vMAJOR` and `vMAJOR.MINOR` tags alongside the full semver tag.

## Adding or Updating a Plugin

Edit `.claude-plugin/marketplace.json`. Each plugin entry requires:
- `name`, `description`, `version`, `author`, `repository`, `license`, `keywords`, `category`
- `source.source` (always `"github"`), `source.repo` (owner/repo format)
- `source.ref` (optional git ref, used when the plugin tag differs from the marketplace tag)

When bumping a plugin version, use `feat` commit type so release-please creates a minor version bump for the marketplace itself.

When adding, removing, or updating plugins in `marketplace.json`, always update the "Available Plugins" table in `README.md` to match.

## Versioning

Releases are automated via release-please. Conventional Commits drive version bumps:
- `feat:` triggers a minor bump
- `fix:` triggers a patch bump

Tags follow the pattern `v1.2.3` with floating `v1` and `v1.2` tags updated on each release.
