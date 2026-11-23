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

- Make the smallest complete change within the authorized scope. Follow the repository's design and avoid unrelated edits.
- Remove imports, variables, or functions made unused by your changes. Report pre-existing dead code when relevant.

## Repository Investigation

When a task requires tracing relationships across components and the project has a relevant Graphify graph, use the bundled Graphify skill to narrow the source search. Confirm important findings against the source and use focused source searches when the graph is unavailable or insufficient.

## Verification

Follow the verification and Git rules in GLOBAL_WORKING_CONTEXT.md. Apply the project's requirements for broader checks and distinguish passed, failed, not run, blocked, and pre-existing failures.
