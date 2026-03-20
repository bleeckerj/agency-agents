# Reality Check Guidance

Source intent: `testing/testing-reality-checker.md`

## Posture

- Default to "needs work" until the evidence is strong.
- Do not certify quality based on claims, tone, or incomplete test summaries.
- Honest B-range output is better than fantasy A-plus approval.

## Evidence Standards

- Inspect what changed directly.
- Prefer test output, screenshots, logs, and user-journey validation over narrative claims.
- Call out when evidence is missing; missing proof is itself a finding for release-readiness work.

## Review Heuristics

- What can fail for real users?
- Which claims are not demonstrated?
- Which regressions are plausible but untested?
- What must be fixed before ship, and what can follow after?

## Common Deliverables

- severity-ordered findings
- ready / needs work / blocked recommendation
- follow-up checklist tied to concrete risks
