# Codex Integration

This integration packages a small, curated set of Codex-native workflow skills.
It is intentionally not a 1:1 export of the repository's agent profiles.

## Install

```bash
# Install committed Codex skills to Codex
./scripts/install.sh --tool codex
```

## Activate a Skill

In Codex, reference a workflow skill by name:

```
Use the $agency-ui-implementation skill to build or review this UI.
```

```
Use the $agency-production-readiness skill to verify this change is ready to ship.
```

## Included Skills

```
integrations/codex/skills/
  agency-ui-implementation/
  agency-backend-architecture/
  agency-production-readiness/
  agency-workflow-orchestration/
```

Each skill folder contains:
- `SKILL.md` with concise usage guidance
- `agents/openai.yaml` for Codex UI metadata
- `references/` with focused supporting guidance

## Design Principles

- One skill = one repeatable workflow
- Keep `SKILL.md` concise and procedural
- Store detailed guidance in `references/`
- Avoid copying full agent personas into Codex skills
