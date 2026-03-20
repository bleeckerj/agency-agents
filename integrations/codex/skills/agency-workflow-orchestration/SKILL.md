---
name: agency-workflow-orchestration
description: Use when the user needs a multi-step delivery plan, work decomposition, role handoffs, or staged execution across specialists. Guides Codex through a quality-gated workflow instead of ad hoc task hopping.
---

# Agency Workflow Orchestration

## When to use

Use this skill for workflow management:
- decomposing large requests into ordered phases
- planning handoffs across roles or specialties
- coordinating implementation, review, and validation steps
- keeping a complex task moving with explicit gates and state

## When not to use

Do not use this skill for:
- single-file implementation tasks
- isolated frontend or backend work that does not need orchestration
- final release review when no workflow coordination is needed

## Inputs expected

Gather these first:
- the goal and acceptance criteria
- current project state and blockers
- major phases or role boundaries
- constraints on time, risk, and validation

## Workflow

1. Define the outcome and the evidence required to call the work complete.
2. Break the task into ordered phases with clear ownership boundaries.
3. Put validation gates between major phases; do not let later work hide earlier quality failures.
4. Track current phase, next action, and blockers explicitly.
5. Keep handoffs short and concrete: what changed, what is still open, and what evidence accompanies the handoff.
6. End with a status summary that makes the next step obvious.

## Checks

- Each phase has a concrete output
- Handoffs preserve the minimum context needed to continue
- Quality gates exist before irreversible or expensive steps
- Blockers and retry paths are explicit
- The plan is actionable, not just aspirational

## Result format

Return:
- current objective
- ordered phases
- validation gate for each phase
- immediate next step
- blockers or escalation paths

## References

- Read `references/orchestration-guidance.md` when you need workflow structure, handoff rules, or quality-gate patterns.
