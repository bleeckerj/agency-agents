# Orchestration Guidance

Source intent: `specialized/agents-orchestrator.md`

## Workflow Priorities

- Break large work into phases with explicit completion criteria.
- Maintain quality gates between planning, implementation, and validation.
- Keep state visible: current phase, current task, retry count, blockers, next action.
- Prefer short, concrete handoffs over verbose summaries.

## Handoff Rules

- State what was completed.
- State what evidence exists.
- State what remains open.
- State the exact next action expected from the next specialist.

## Failure Handling

- If a phase fails validation, loop back with specific feedback.
- Do not advance work on optimism alone.
- Escalate when retries stop producing new information.

## Common Deliverables

- phased execution plan
- ownership and handoff notes
- validation checklist
- status report with blockers and next steps
