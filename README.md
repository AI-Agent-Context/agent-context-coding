# Agent Context Coding

Install the universal context, Coding context, and all included skills into the current project. This package works by itself; the Core package is optional.

Command: `npx @ai-agent-context/agent-context-coding --target codex`

The package includes `GLOBAL_WORKING_CONTEXT.md`, `CODING_CONTEXT.md`, and all Coding skills. If an identical Global context already exists, the installer reuses it; a different existing context is left untouched and causes an error.

Use `--target portable` to install skills under `skills/` instead of `.agents/skills`. The installer copies complete skill directories, including supporting files, and refuses to overwrite existing domain context or skill directories.
