# Agent Guide

## Purpose

This repo maintains an agent-friendly Tailwind CSS v4 docs snapshot.
The goal is to keep the skill current and easy to install in any agent.

## Key paths

- Skill root: `skills/tailwind-4-docs/`
- Docs snapshot: `skills/tailwind-4-docs/references/docs/`
- Docs index map: `skills/tailwind-4-docs/references/docs-index.tsx`
- Snapshot metadata: `skills/tailwind-4-docs/references/docs-source.txt`
- Gotchas: `skills/tailwind-4-docs/references/gotchas.md`
- Sync script: `skills/tailwind-4-docs/scripts/sync_tailwind_docs.py`

## Update rules

- Do not hand-edit the MDX docs snapshot. Always refresh via the sync script.
- Keep `docs-source.txt` in sync with the snapshot commit.
- Prefer minimal edits to `SKILL.md` and `gotchas.md` when guidance changes.
- Use ASCII when editing unless the file already contains non-ASCII content.

## Sync docs snapshot

Use the local clone if available (faster, deterministic):

```
python skills/tailwind-4-docs/scripts/sync_tailwind_docs.py --local-repo tmp-tailwindcss.com
```

If the local clone is missing, run without `--local-repo` to clone a temp copy.

## Maintenance checklist

- Verify the snapshot commit updated in `docs-source.txt`.
- Scan docs for major v4 changes and update `gotchas.md` if needed.
- If you install the skill locally, restart or reload your agent to load it.
