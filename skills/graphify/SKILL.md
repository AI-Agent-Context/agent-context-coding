---
name: graphify
description: Build, refresh, or query a local Graphify code graph to locate components, dependencies, and relevant source files.
---

# Graphify

This Coding skill wraps the official [Graphify CLI](https://github.com/Graphify-Labs/graphify). Work from the target project root.

## Setup

If the CLI is unavailable and setup is part of the task, install the official Python package in an isolated tool environment with `uv tool install graphifyy` or `pipx install graphifyy`. Check `graphify --help` for the installed version's commands. Coding supplies this skill and its routing. A separate assistant integration is optional.

## Workflow

1. For a code relationship question, reuse the project's existing graph if it covers the relevant files. Run a focused query with `graphify query "<question>"`, `graphify path "<node A>" "<node B>"`, or `graphify explain "<node>"`.
2. To build or refresh a graph within the task scope, run `graphify extract . --code-only`. Scope the scan to the authorized project or directory and honor ignore rules. Use local code extraction by default. Semantic extraction using an external provider requires authorization to send the selected material. Keep generated graph files local unless sharing is authorized.
3. Open the relevant source to confirm important relationships, especially inferred edges or edges from a stale graph. If the CLI, graph, or coverage is unavailable, continue with targeted source searches.
