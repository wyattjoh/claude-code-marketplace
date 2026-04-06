# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A Claude Code plugin marketplace registry. The core artifact is `.claude-plugin/marketplace.json`, which lists available plugins with their metadata and source repositories. There is no application code to build, lint, or test.

## Key Files

- `.claude-plugin/marketplace.json` - The marketplace manifest. Each entry in the `plugins` array defines a plugin's name, version, description, source repo, and optional git ref.
- `README.md` - Includes an "Available Plugins" table that must stay in sync with the manifest.

## Adding or Updating a Plugin

Edit `.claude-plugin/marketplace.json`. Each plugin entry requires:
- `name`, `description`, `version`, `author`, `repository`, `license`, `keywords`, `category`
- `source.source` (always `"github"`), `source.repo` (owner/repo format)
- `source.ref` (optional git ref, used when the plugin tag differs from the marketplace tag)

When adding, removing, or updating plugins in `marketplace.json`, always update the "Available Plugins" table in `README.md` to match.
