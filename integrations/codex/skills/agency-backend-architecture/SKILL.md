---
name: agency-backend-architecture
description: Use when the user needs backend architecture, API design, schema planning, service decomposition, or system trade-off analysis. Guides Codex through pragmatic server-side design with explicit constraints and consequences.
---

# Agency Backend Architecture

## When to use

Use this skill for backend and system-design work:
- API and service design
- schema and persistence planning
- architecture reviews and refactors
- trade-off analysis for scaling, reliability, and maintainability

## When not to use

Do not use this skill for:
- frontend implementation details
- release readiness sign-off
- general project orchestration unless the task is specifically architectural planning

## Inputs expected

Collect these first:
- product requirements and request flow
- current system boundaries and major dependencies
- scale, latency, consistency, and security constraints
- existing schema, API, or deployment assumptions

## Workflow

1. Define the problem in terms of domain boundaries, request flows, and constraints.
2. Inspect the current implementation before proposing new abstractions.
3. Present the preferred architecture in concrete terms: components, interfaces, data shape, and ownership boundaries.
4. Name the main trade-offs and rejected alternatives.
5. Keep the design reversible where possible and avoid architecture that exceeds the team's likely operating complexity.
6. Provide implementation guidance that an engineer can apply without inventing missing details.

## Checks

- Names the important trade-offs, not just the preferred design
- Fits the current product and team complexity
- Covers data shape, boundaries, and failure modes
- Accounts for security, observability, and performance basics
- Avoids unnecessary distributed-system complexity

## Result format

Return:
- recommended architecture or change
- rationale and trade-offs
- concrete interface or schema impacts
- implementation order and major risks

## References

- Read `references/backend-guidance.md` when you need architecture patterns, decision framing, or server-side review heuristics.
