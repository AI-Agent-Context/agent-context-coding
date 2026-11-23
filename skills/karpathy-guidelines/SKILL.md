---
name: karpathy-guidelines
description: Behavioral guidelines to prevent common LLM coding pitfalls, enforce simplicity, and ensure surgical edits.
---

# Skill: karpathy-guidelines

Behavioral guidelines to reduce common LLM coding mistakes, derived from Andrej Karpathy's observations on LLM coding pitfalls. Use this skill when writing, reviewing, or refactoring code to avoid overcomplication, make surgical changes, surface assumptions, and define verifiable success criteria.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## Workflow & The Four Principles

### Phase 1 — Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what is confusing. Ask.

### Phase 2 — Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that was not requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### Phase 3 — Surgical Changes

**Touch only what you must. Clean up only your own mess.**

Apply the Code Changes rules in the Coding Working Context.

The test: Every changed line must trace directly to the authorized user request.

### Phase 4 — Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

## Deliverables & Expected Output

Deliver the outcome directly in conversation:
- **Clarifications & Tradeoffs**: Explicit assumptions and confirmed decisions.
- **Surgical Diff**: The minimal code changes made, strictly matching the requested scope.
- **Verification Evidence**: Test results and execution logs proving all acceptance criteria pass.

Do not create an unsolicited report file.

## Verification & Completion Criteria

- **Verified Goals**: All stated goals have been verified with passing checks.
- **Simplicity Review**: Code contains no speculative abstractions or single-use bloat.
- **Zero Collateral Edits**: All adjacent formatting, unrelated comments, and orthogonal logic remain untouched.
