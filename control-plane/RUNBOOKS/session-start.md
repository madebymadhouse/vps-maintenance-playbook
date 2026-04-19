# Session Start

## Purpose

Make each working session start from verified state instead of memory.

## Preconditions

- Workspace is open at `/home/samhcharles`
- You know whether the task is Windows, WSL, VPS, or cross-machine

## Steps

1. Read `/home/samhcharles/control-plane/CURRENT_STATE.md`
2. Read `/home/samhcharles/control-plane/TOPOLOGY.md`
3. Read `/home/samhcharles/control-plane/WORKFLOWS.md`
4. If the task touches code, draft from `TEMPLATES/HANDOFF_TEMPLATE.md`
5. If the task touches runtime, check whether a runbook already exists
6. State the task in one line:
   - machine in scope
   - repo or service in scope
   - target outcome
   - verification method
7. Only then begin execution or delegation

## Verification

You should be able to answer these four questions before work starts:

1. Which machine is authoritative for this task?
2. Which repo or service is in scope?
3. What proves success?
4. What doc must be updated when done?

## Failure Handling

- If any of the four answers are unclear, stay in planning mode
- Do not send a coding agent into a repo until the handoff is written

## Afterward

- Update `CURRENT_STATE.md` if the live understanding changed
- Add or improve a runbook if the session exposed repeated confusion
