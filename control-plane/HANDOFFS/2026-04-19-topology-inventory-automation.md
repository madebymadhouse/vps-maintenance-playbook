# Coding Handoff: Topology Inventory Automation

## Goal

Create a small, safe inventory script that snapshots key VPS topology facts into a dated audit file for the control plane.

## Scope

- Machine in scope: VPS
- Repo path: `/home/samhcharles/control-plane`
- Files or directories likely involved:
  - `AUDITS/`
  - `RUNBOOKS/vps-audit.md`
  - new script path such as `scripts/` or `tools/`

## Verified Inputs

- Relevant docs already read:
  - `README.md`
  - `TOPOLOGY.md`
  - `RUNBOOKS/vps-audit.md`
  - `AUDITS/2026-04-19-vps-audit.md`
- Known constraints:
  - The script must be read-only
  - The script must not require root
  - The output should be human-readable Markdown or plain text
  - The script should tolerate missing tools gracefully
- Existing behavior:
  - Inventory is currently gathered manually through ad hoc shell commands
  - Topology drift is easy because there is no repeatable snapshot tool yet

## Non-Goals

- Do not restart services
- Do not mutate Docker state
- Do not rewrite topology automatically
- Do not inspect secret values from `.env` files

## Success Criteria

1. Running the script creates a dated audit snapshot with services, containers, key paths, timers, and repo state
2. The script exits successfully even when one category cannot be collected
3. `RUNBOOKS/vps-audit.md` is updated with how to run the script

## Deliverables

- changed files
- verification results
- blockers, if any