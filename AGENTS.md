# Agent Guide

## Purpose

This repo maintains an agent-friendly Tailwind CSS v4 docs workflow.
The goal is to keep the skill current and easy to install in any agent without bundling the upstream docs.

## Key paths

- Skill root: `skills/tailwind-4-docs/`
- Docs snapshot (generated locally): `skills/tailwind-4-docs/references/docs/`
- Docs index map (generated locally): `skills/tailwind-4-docs/references/docs-index.tsx`
- Snapshot metadata: `skills/tailwind-4-docs/references/docs-source.txt`
- Engineering playbook: `skills/tailwind-4-docs/references/engineering-playbook.md`
- Gotchas: `skills/tailwind-4-docs/references/gotchas.md`
- Sync script: `skills/tailwind-4-docs/scripts/sync_tailwind_docs.py`

## Update rules

- Do not hand-edit the MDX docs snapshot. Always refresh via the sync script.
- Do not commit the downloaded docs or docs index to the repo.
- Keep `docs-source.txt` in sync with the snapshot commit (or the uninitialized placeholder).
- Prefer minimal edits to `SKILL.md`, `references/engineering-playbook.md`, and `gotchas.md` when guidance changes.
- Keep the skill framework-agnostic. Do not add Orchard Core, Razor, Liquid, or other product-specific concepts unless the skill is intentionally being specialized for that ecosystem.
- Use ASCII when editing unless the file already contains non-ASCII content.

## Sync docs snapshot

Use the local clone if available (faster, deterministic):

```
python skills/tailwind-4-docs/scripts/sync_tailwind_docs.py --accept-docs-license --local-repo tmp-tailwindcss.com
```

If the local clone is missing, run without `--local-repo` to clone a temp copy.

## Maintenance checklist

- Verify the snapshot commit updated in `docs-source.txt`.
- Scan docs for major v4 changes and update `gotchas.md` if needed.
- Keep `references/engineering-playbook.md` aligned with the official docs structure and practical implementation guidance.
- If you install the skill locally, restart or reload your agent to load it.
