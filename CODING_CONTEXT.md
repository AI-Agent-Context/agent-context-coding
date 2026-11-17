# Coding Working Context

---

## Purpose & Scope

This document provides domain-specific standards for **Software Engineering and Coding** workflows. It extends the universal principles defined in `GLOBAL_WORKING_CONTEXT.md`.

---

## Code Quality

### General Principles

- **Readability**: Code should be clear, intentional, and self-documenting.
- **Consistency**: Follow existing conventions, naming styles, and patterns in the repository.
- **Simplicity**: Prefer straightforward, simple solutions over speculative or over-engineered abstractions. Do not create abstractions for single-use code.
- **Minimal Surface**: If 50 lines cleanly solve the problem, do not write 200 lines.

### Error Handling

- **Meaningful messages**: Provide informative error messages with sufficient context for debugging.
- **Proper status codes**: Use appropriate HTTP, exit, or domain-specific error codes.
- **Log with context**: Log errors with actionable details without exposing secrets or credentials.

### Docker & Container Logs

- Start with a bounded recent sample by default: `docker logs <container-name> --tail 100`.
- If that sample omits necessary evidence, expand the bounded range or use targeted timestamps and filters. Gather enough evidence for a correct diagnosis rather than treating 100 lines as a hard limit.
- Avoid unbounded or unnecessarily large output. Do not use real-time following (`-f`) by default.

---

## Code Changes

- **Minimal changes**: Only modify what is strictly necessary to fulfill the authorized task.
- **Follow existing patterns**: Adhere to existing architectural style, directory layout, and language idiom.
- **Surgical edits**: Do not reformat, refactor, or "improve" adjacent or orthogonal code outside the task scope.
- **Clean up own orphans**: Remove unused imports, variables, or functions created by your changes, but do not remove pre-existing dead code without authorization.
- **No unrequested refactoring**: Never modify, format, or restructure existing code outside the approved task.

---

## Testing & Verification Rule

- Run checks and tests directly relevant to the change before reporting completion.
- Run the full test suite when required by the project context or before major integration.
- If a check fails:
  1. Diagnose the root cause.
  2. Fix it within the authorized scope when possible.
  3. Otherwise, report the failure and blocker clearly with exact error logs and reproduction steps.
- Distinguish test results clearly: `passed`, `failed`, `not run`, `blocked`, and `pre-existing failures`.
- Do not claim a pass, commit, or push while required checks fail or remain blocked. Pre-existing failures are not an automatic exemption.

---

## Git Workflow for Code

- Staged changes must be thoroughly reviewed with `git diff --staged` before committing.
- Commit messages must follow **Conventional Commits**:
  - `feat`: New feature
  - `fix`: Bug fix
  - `docs`: Documentation changes
  - `refactor`: Code refactoring (no functional change)
  - `test`: Adding or updating tests
  - `style`: Code style / formatting changes
  - `chore`: Maintenance, dependencies, build config
- Never commit secrets, tokens, `.env` files, credentials, or private keys.
