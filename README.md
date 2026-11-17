# Agent Context Coding

Install the shared Core context, coding context, and coding skills into the current project.

## Install

Run from the root of the project where you want the files:

    npx @ai-agent-context/agent-context-coding

npm installs Core as a dependency, so you do not need to install Core separately. The command copies:

- `GLOBAL_WORKING_CONTEXT.md` from Core into the project root.
- `CODING_CONTEXT.md` into the project root.
- The included skills into `.agents/skills/<skill-name>/`.

Requires Node.js `^18.17.0` or `>=20.5.0`. The installer does not change agent-wide settings or load context automatically.

## Included skills

The package installs all of these skills:

| Skill | What it does |
|---|---|
| `diagnose-bug` | Investigates a reported bug, verifies its root cause, and checks an authorized fix. |
| `implement-feature` | Implements an agreed feature and verifies its acceptance criteria. |
| `karpathy-guidelines` | Keeps coding work simple, focused, and explicit about assumptions. |
| `optimize-performance` | Measures a performance bottleneck and checks an optimization against a baseline. |
| `plan-feature` | Turns a feature request into an evidence-based plan before implementation. |
| `refactor-code` | Restructures code while preserving observable behavior and checking regressions. |
| `review-architecture` | Assesses system boundaries, dependencies, and failure scenarios against project goals. |
| `review-code` | Reviews a concrete code change for correctness and regression defects. |
| `review-security` | Reviews a specified code or configuration area for security weaknesses. |
| `setup-project` | Sets up or repairs the local development environment and verifies the setup path. |
| `write-tests` | Adds behavior-focused automated tests for requirements, regressions, or coverage gaps. |

## Load context for a session

At the start of each session, load or attach `GLOBAL_WORKING_CONTEXT.md`. For software engineering work, also load `CODING_CONTEXT.md` and use the relevant coding skills from `.agents/skills/`.

## Portable skills directory

To put skills under `skills/` instead of `.agents/skills/`, run:

    npx @ai-agent-context/agent-context-coding --target portable

The context files remain in the project root.

## Existing files

The installer never overwrites project files or skill directories. It reuses `GLOBAL_WORKING_CONTEXT.md` only when the existing file is identical to Core's copy. A different Global Working Context, an existing `CODING_CONTEXT.md`, or a directory already present for one of the included skills stops the installation; resolve the conflict before retrying.

## Install only Core

To copy only the shared Global Working Context, run:

    npx @ai-agent-context/agent-context-core

This does not install `CODING_CONTEXT.md` or coding skills.
