# Lombiq Tailwind Agent Skills

## About

This repository contains [agent skills](https://agentskills.io/home) for Tailwind v4 development tasks. With these skills, you can use your favorite agent efficiently for Tailwind v4 usage, configuration, and migration questions, and initialize a local docs snapshot after installation.

Do you want something similar for Orchard Core? Check out [Lombiq Orchard Core Agent Skills](https://github.com/Lombiq/Orchard-Core-Agent-Skills)!

## Requirements

- Any agent that supports agent skills.
- For one-command installation with `npx skills add`, install Node.js (includes `npx`).
- The `tailwind-4-docs` skill includes a Python script for syncing the docs snapshot. You can run the script manually, but it provides a convenient way to initialize or refresh the snapshot after installation. To use it:
  - Install Python 3.8 or later (available on `PATH`).
  - Install `git` (available on `PATH`).
  - Enable internet access for the agent.
  - Ensure the installed skill folder is writable.

## Skills included

### `tailwind-4-docs`

An agent-optimized workflow for Tailwind CSS v4 documentation, including a curated gotchas list, an implementation playbook, and a local docs snapshot generator. Your agent should use this during Tailwind 4 development-related tasks.

#### Highlights

- Mirrors the official Tailwind docs structure so agents can load only what they need after initialization.
- Generates `docs-index.tsx` locally to map categories and slugs to MDX files.
- Includes an agent-oriented engineering playbook for implementation, refactor, and review tasks.
- Provides a sync script that can initialize and refresh references after installation.
- Does not bundle the Tailwind docs themselves due to upstream licensing.

#### Initialization and updates

**IMPORTANT**: Initialize the docs snapshot after installation. If your agent does not do this automatically, ask it to run the sync script (or run it manually). If the snapshot is missing or older than one week, run the sync script before relying on the docs.

Some agents do not run scripts automatically even if the `SKILL.md` asks for it. If the snapshot is missing or older than one week, explicitly instruct the agent to run the sync command and confirm that `references/docs/` and `references/docs-index.tsx` were created.

To initialize the snapshot manually, run `python skills/tailwind-4-docs/scripts/sync_tailwind_docs.py --accept-docs-license`. If you already have a local clone of the source repository, add `--local-repo <path>`.

The script clones `tailwindcss.com` into a temporary folder (or uses the local repo if provided), then copies:
  - `src/docs/` to `skills/tailwind-4-docs/references/docs/`
  - `src/docs/docs-index.tsx` to `skills/tailwind-4-docs/references/docs-index.tsx`
  - the snapshot date and the upstream commit hash to `skills/tailwind-4-docs/references/docs-source.txt`

License note: The Tailwind docs repo is source-available and explicitly not open source. This repository does not redistribute the docs. Users are responsible for accepting the upstream license before downloading the snapshot.

## Installing skills

The quickest way to install from this repository is to use the `skills` CLI, which detects and installs skills automatically.

```bash
npx skills add Lombiq/Tailwind-Agent-Skills
```

If you prefer manual installation, copy the `skills/` subfolders into your agent's skills directory:
- Project scope: `.github/skills/` (Copilot), `.codex/skills/` (Codex), `.claude/skills/` (Claude Code)
- Global scope: `~/.copilot/skills/`, `~/.codex/skills/`, `~/.claude/skills/` (or `%USERPROFILE%\\...\\skills` on Windows)

For GitHub Copilot in VS Code, Agent Skills are currently in preview and available only after enabling `chat.useAgentSkills`. See [the docs](https://docs.github.com/copilot/concepts/agents/about-agent-skills).

## Contributing

Bug reports, feature requests, comments, questions, code contributions and love letters are warmly welcome. You can send them to us via GitHub issues and pull requests. Please adhere to our [open-source guidelines](https://lombiq.com/open-source-guidelines) while doing so.

This project is developed by [Lombiq Technologies](https://lombiq.com/). Commercial-grade support is available through Lombiq.
