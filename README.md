# Agent Context Coding

Install the Coding context and skills. npm also installs Core as a dependency, so Global Working Context stays sourced from the Core package.

Command: `npx @ai-agent-context/agent-context-coding --target codex`

This command installs GLOBAL_WORKING_CONTEXT.md from Core, CODING_CONTEXT.md, and all Coding skills. If an identical Global context already exists, it is reused; a different existing file is left untouched and causes an error.

Running `npx @ai-agent-context/agent-context-core` by itself installs only Global Working Context.

Use `--target portable` to install skills under `skills/` instead of `.agents/skills`. The installer copies complete skill directories, including supporting files, and refuses to overwrite existing domain context or skill directories.
