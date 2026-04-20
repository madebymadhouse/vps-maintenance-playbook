# Start Here For Agents

Read this before doing VPS work.

Your job is not to guess. Your job is to understand what is running, inspect it safely, make the smallest correct change, and leave the docs clearer than you found them.

## Required First Reads

1. `CURRENT_STATE.md`
2. `TOPOLOGY.md`
3. `WORKFLOWS.md`
4. Relevant runbook in `RUNBOOKS/`
5. `TEMPLATES/HANDOFF_TEMPLATE.md` if code changes are needed

## Questions To Answer Before Acting

1. Is this task inspect, change, or recover?
2. What service or repo is in scope?
3. What will prove success?
4. What is the safest way to verify the result?
5. Which document needs an update when the work is done?

## Rules

- Prefer verified facts over assumptions
- If the current state is unclear, audit first
- Keep observation separate from mutation
- Do not make repo code changes without a written handoff
- Leave behind the state needed for the next operator

## Path Notes

Examples in this repo use one real environment. If you copy this pattern for your own server, replace the paths and service names with your own.