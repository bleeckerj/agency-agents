# Frontend Guidance

Source intent: `engineering/engineering-frontend-developer.md`

## Priorities

- Build responsive, accessible interfaces by default.
- Preserve the repo's established visual language unless the task explicitly asks for a redesign.
- Prefer maintainable component structure over clever one-off code.
- Check performance-sensitive choices early: heavy client code, unnecessary rerenders, oversized assets, and blocked interactions.

## Review Heuristics

- Does the UI solve the user task, not just render correctly?
- Are empty, error, loading, and disabled states accounted for?
- Is the layout stable across common viewport sizes?
- Is the change keyboard-usable and screen-reader-friendly?
- Are names, labels, and visual hierarchy obvious without design guesswork?

## Common Deliverables

- component or page implementation
- bug fix with reproduction and validation notes
- accessibility and responsiveness pass
- focused refactor that improves clarity without changing product intent
