# Tailwind Agent Skills

## About

This repository contains [agent skills](https://agentskills.io/home) for Tailwind v4 development tasks. With these skills, you can use your favorite agent efficiently for Tailwind v4 usage, configuration, and migration questions, and initialize a local docs snapshot after installation.

## Skills included

### `tailwind-4-docs`

An agent-optimized workflow for Tailwind CSS v4 documentation, including a curated gotchas list and a local docs snapshot generator.

Highlights:
- Mirrors the official Tailwind docs structure so agents can load only what they need after initialization.
- Generates `docs-index.tsx` locally to map categories and slugs to MDX files.
- Provides a sync script that can initialize and refresh references after install.
- Does not bundle the Tailwind docs themselves due to upstream licensing.

## Installing skills

The skills are agent-agnostic, but each agent has its own discovery locations. Here are concise setups for common agents:

### GitHub Copilot (coding agent, Copilot CLI, VS Code agent mode)

- VS Code reads skills from the workspace (repository). Place the skill folders into the `.github/skills/` directory (recommended).
- Skills placed under `.claude/skills/` are also detected for backward compatibility.
- For personal (global) skills used by Copilot CLI or the Copilot coding agent, place them in `~/.copilot/skills` or `~/.claude/skills`. On Windows, use `%USERPROFILE%\.copilot\skills` or `%USERPROFILE%\.claude\skills`.
- VS Code Agent Skills are currently in preview and only available in VS Code Insiders; enable `chat.useAgentSkills` to use them.
- Docs: https://docs.github.com/copilot/concepts/agents/about-agent-skills

### OpenAI Codex (CLI and IDE extensions)

- Place the skill folders into one of the following locations inside your repository. Codex checks these in order, from highest to lowest priority:
  ```text
  $CWD/.codex/skills
  $CWD/../.codex/skills
  $REPO_ROOT/.codex/skills
  ```
- To make the skills available across all repositories on your machine, place them into `$CODEX_HOME/skills`. On macOS and Linux this defaults to `~/.codex/skills`.
- Docs: https://developers.openai.com/codex/skills

### Anthropic Claude Code

- To use skills in a single repository or workspace, place the skill folders into `.claude/skills/`.
- To make the skills available globally for all projects, place them into `~/.claude/skills/`.
- Some Claude plugins include and manage their own skills automatically.
- Docs: https://code.claude.com/docs/en/skills

## Initializing or updating the docs snapshot after install

This skill can initialize or refresh its own references even after you install it. Ask your agent to run the sync script from the installed skill folder.

How it works (handled by the agent when you ask):
- It runs the `skills/tailwind-4-docs/scripts/sync_tailwind_docs.py` script with `--accept-docs-license`.
- Clones `tailwindcss.com` into a temp folder (or uses `--local-repo` if provided).
- Copies `src/docs/` into `skills/tailwind-4-docs/references/docs/`.
- Copies the docs index to `skills/tailwind-4-docs/references/docs-index.tsx`.
- Records the upstream commit in `skills/tailwind-4-docs/references/docs-source.txt`.

This works in real life as long as the installed skill folder is writable, the agent has internet access, and the user can run the script. The skill content updates in place, so future reads use the latest docs snapshot.

Some agents will not run scripts automatically even if the skill asks for it. If the snapshot is missing, explicitly instruct the agent to run the sync command and confirm that `references/docs/` and `references/docs-index.tsx` were created.

Note: The Tailwind docs repo is source-available and explicitly not open-source. This repository does not redistribute the docs. Users are responsible for accepting the upstream license before downloading the snapshot.

## Contributing

Bug reports, feature requests, comments, questions, code contributions and love letters are warmly welcome. You can send them to us via GitHub issues and pull requests. Please adhere to our [open-source guidelines](https://lombiq.com/open-source-guidelines) while doing so.

This project is developed by [Lombiq Technologies](https://lombiq.com/). Commercial-grade support is available through Lombiq.
