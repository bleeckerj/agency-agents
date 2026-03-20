# Backend Guidance

Source intent:
- `engineering/engineering-backend-architect.md`
- `engineering/engineering-software-architect.md`

## Architecture Priorities

- Security first: least privilege, encryption, safe defaults, and clear trust boundaries.
- Performance-conscious design: query shape, indexing, caching, and failure behavior should be part of the design, not deferred.
- Reliability matters: include degradation paths, retries, circuit breakers, and observability where the change warrants them.

## Decision Heuristics

- Prefer the simplest architecture that can survive expected growth.
- Name trade-offs explicitly: consistency vs availability, coupling vs duplication, simplicity vs flexibility.
- Domain first, technology second. Match the architecture to the problem and team.
- Favor reversibility over premature optimization.

## Common Deliverables

- API shape and resource boundaries
- schema or storage design
- service decomposition plan
- ADR-style recommendation with consequences
