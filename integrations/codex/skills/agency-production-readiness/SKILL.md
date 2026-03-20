---
name: agency-production-readiness
description: Use when the user wants a skeptical release-readiness review, validation of claims, or a final pass on correctness, quality, and risk. Guides Codex to default to evidence over optimism and to require concrete proof before approval.
---

# Agency Production Readiness

## When to use

Use this skill for final review and release-readiness work:
- verifying whether a change is actually ready to ship
- challenging optimistic claims with evidence
- reviewing tests, user journeys, and failure modes
- producing a realistic go or no-go recommendation

## When not to use

Do not use this skill for:
- initial implementation of a feature
- broad architectural planning
- coordination of multi-step delivery work

## Inputs expected

Collect these first:
- the code diff or changed files
- available test results, screenshots, logs, and reproduction steps
- claimed acceptance criteria or production-readiness statements
- known risks, rollout assumptions, and missing coverage

## Workflow

1. Start from skepticism. Assume the change needs work until evidence proves otherwise.
2. Verify what actually changed instead of relying on summaries.
3. Cross-check claims against code, test output, and user-visible behavior.
4. Focus on concrete risks: regressions, missing tests, broken flows, unsupported assumptions, and operational gaps.
5. Separate critical blockers from medium-risk follow-up items.
6. Conclude with a realistic status: ready, needs work, or blocked.

## Checks

- Claims are backed by code or test evidence
- Key user journeys and failure paths are covered
- Missing tests or missing validation are called out explicitly
- Severity is realistic, not inflated and not softened
- Final recommendation is defensible from the evidence shown

## Result format

Return:
- findings ordered by severity
- the evidence each finding is based on
- final readiness status
- exact follow-up needed before approval

## References

- Read `references/reality-check-guidance.md` when you need review posture, evidence standards, or release-readiness heuristics.
