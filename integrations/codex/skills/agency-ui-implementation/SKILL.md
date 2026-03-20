---
name: agency-ui-implementation
description: Use when the user needs frontend implementation, UI review, responsive fixes, or accessibility and performance improvements for a web interface. Guides Codex through scoped UI delivery with evidence-backed checks.
---

# Agency UI Implementation

## When to use

Use this skill for frontend implementation and review work:
- building or refining components, pages, and interaction flows
- fixing layout, responsive, accessibility, or performance issues
- translating a design brief into concrete UI changes

## When not to use

Do not use this skill for:
- backend architecture or data modeling
- final production sign-off
- multi-agent workflow coordination across the whole project

## Inputs expected

Gather these before editing:
- the target files or feature area
- the design intent, acceptance criteria, or bug report
- framework and styling constraints already present in the repo
- screenshots or reproduction steps when the task is a bug fix

## Workflow

1. Inspect the relevant UI files, routes, and styling system before proposing changes.
2. Restate the user-visible goal in implementation terms: behavior, layout, states, and constraints.
3. Preserve the existing design system unless the task explicitly asks for a new visual direction.
4. Make the smallest coherent change set that resolves the issue end to end.
5. Verify responsive behavior, keyboard access, semantic structure, and obvious loading/error states.
6. Report what changed, what was validated, and any residual UI risks.

## Checks

- Matches the requested behavior and scope
- Works on desktop and mobile layouts
- Uses semantic HTML and keyboard-accessible controls
- Avoids obvious performance regressions and broken states
- Keeps changes consistent with existing project patterns

## Result format

Return:
- a short summary of the UI change
- the main files changed
- what was verified
- any remaining edge cases or follow-up items

## References

- Read `references/frontend-guidance.md` when you need implementation priorities, review heuristics, or frontend-specific acceptance checks.
