# Workflows

## Default Flow

1. Start with `CURRENT_STATE.md` and `TOPOLOGY.md`
2. Decide whether the task is inspect, change, or recover
3. Read the matching runbook if one exists
4. Verify the current state before touching anything
5. Make the smallest correct change
6. Verify the result
7. Update the docs if the live state or known process changed

## Inspect

Use this for audits, logs, runtime checks, and questions about what is running.

Rules:
- prefer read-only commands
- record verified facts, not guesses
- update topology or current state when you learn something important

## Change

Use this for deploys, config changes, migrations, and code-related maintenance.

Rules:
- start from the current verified state
- use a handoff contract before repo code changes
- keep the change narrow and verify it before stopping

## Recover

Use this for outages, bad deploys, failed migrations, and rollback work.

Rules:
- stabilize first
- prefer runbook steps over improvisation
- write down what happened, what was changed, and what still needs follow-up

## Anti-Drift Rules

- Do not rely on chat as the only record
- Do not mix guesses with verified runtime facts
- Do not make code changes without a clear scope and handoff
- Do not finish a VPS task without leaving behind updated notes when needed
