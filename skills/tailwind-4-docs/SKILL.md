---
name: tailwind-4-docs
description: Comprehensive Tailwind CSS v4 documentation snapshot and workflow guidance. Use when answering Tailwind v4 questions, selecting utilities/variants, configuring Tailwind v4, or migrating projects from v3 to v4 with official docs and gotcha checks.
---

# Tailwind 4 Docs

## Overview

Use this skill to navigate the Tailwind CSS v4 documentation snapshot and answer development, configuration, and migration questions with official guidance.

## Quick start

1. Identify the topic (utility, variant, config, migration, compatibility).
2. Find the matching doc in `references/docs-index.tsx`.
3. Load only the relevant file from `references/docs/`.
4. Apply guidance and call out any breaking changes or constraints.

## References map

- `references/docs/` contains the Tailwind v4 MDX docs snapshot from tailwindcss.com.
- `references/docs-index.tsx` contains the category and slug map used by the docs sidebar.
- `references/docs-source.txt` captures the upstream repo, commit, and snapshot date.
- `references/gotchas.md` provides a quick scan of common v4 migration pitfalls.

## MDX handling

- Treat `export const title` and `export const description` as metadata.
- Read JSX callouts like `<TipInfo>` or `<TipBad>` as guidance text.

## Common entry points

- Migration: `references/docs/upgrade-guide.mdx`, `references/docs/compatibility.mdx`.
- Gotchas overview: `references/gotchas.md`.
- Configuration and directives: `references/docs/functions-and-directives.mdx`, `references/docs/adding-custom-styles.mdx`, `references/docs/theme.mdx`.
- Variants and responsive patterns: `references/docs/hover-focus-and-other-states.mdx`, `references/docs/responsive-design.mdx`.
- Core behavior: `references/docs/preflight.mdx`, `references/docs/detecting-classes-in-source-files.mdx`.

## Migration checklist

When upgrading from v3 to v4, always confirm the following in the docs:

- Browser support and compatibility expectations.
- Tooling changes: `@tailwindcss/postcss`, `@tailwindcss/cli`, `@tailwindcss/vite`.
- Import syntax: `@import "tailwindcss"` replaces `@tailwind` directives.
- Utility renames/removals, prefix format, and important modifier placement.
- Changes to variants, transforms, and arbitrary value syntax.

## Update workflow

Run `scripts/sync_tailwind_docs.py` to refresh the snapshot. Use `--local-repo` if you already have a local clone of `tailwindlabs/tailwindcss.com` to speed up syncs.

---
