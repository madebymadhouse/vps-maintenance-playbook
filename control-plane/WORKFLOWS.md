# Workflows

## Default Task Flow

1. Start in the control plane
2. Identify machine in scope
3. Read current state and topology
4. Produce a short plan
5. Decide whether the task is planning, implementation, or runtime maintenance
6. If implementation is needed, write a handoff contract
7. Execute or delegate
8. Record outcome back in the control plane

## Task Lanes

### Planning Lane

Use when the problem is unclear, spread across machines, or likely to confuse agents.

Outputs:
- clarified scope
- verified facts
- gaps list
- immediate plan
- documentation updates

### Implementation Lane

Use when the target repo and change are already clear.

Rules:
- must begin with a handoff contract
- must name files, constraints, and success criteria
- must record verification outcome afterward

### Runtime Maintenance Lane

Use for VPS checks, deploys, logs, backups, migrations, and service recovery.

Rules:
- prefer runbook-driven work
- distinguish observation from mutation
- leave behind a state update if live behavior changed

## Anti-Drift Rules

- Do not use chat history as the only durable plan
- Do not send a coding agent into a repo without a contract
- Do not let live VPS state become the only record of how something works
- Do not mix speculative design with production maintenance in the same step

## Weekly Ritual

Once per week:

1. Review `CURRENT_STATE.md`
2. Prune stale plans
3. Add missing runbooks discovered during the week
4. Tighten agent boundaries where confusion occurred
5. Record one lesson that would have saved time earlier
