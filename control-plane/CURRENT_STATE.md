# Current State

Last updated: 2026-04-19

## Objective

Create a stable control plane for development and VPS maintenance so agentic work stops depending on fragile chat context.

## Verified Facts

- Main workspace root is `/home/samhcharles`
- OpenClaw agent framework exists in `/home/samhcharles/repos/hank-duck/openclaw`
- Live Discord bot workspace exists in `/home/samhcharles/srv/bots/chopsticks-lean`
- The chopsticks lean deployment is intentionally VPS-friendly and simple
- The OpenClaw coder workflow is strict, contract-driven, and expects explicit plan and memory files
- There was no existing workspace-level custom agent folder before this setup

## Active Problems

- Workflow knowledge is scattered across repos, chat history, and machine-specific context
- Agent behavior is inconsistent because the first-read context is not centralized
- Planning, implementation, and runtime maintenance are too easy to blend together
- Cross-machine responsibilities are not yet codified in one place

## Immediate Direction

- Use this `control-plane` folder as the first landing zone for future agent work
- Use the `VPS Maintenance Planner` agent for topology, workflow, and maintenance planning tasks
- Require any implementation-heavy agent to receive a written handoff contract
- Use `AUDITS/2026-04-19-vps-audit.md` as the baseline verified VPS inventory snapshot
- Use `AUDITS/2026-04-19-vps-audit-followup.md` as the deeper snapshot for empty placeholder paths, Docker volumes, and port exposure

## Near-Term Milestones

1. Decide whether empty paths under `/home/samhcharles/srv/agents`, `/home/samhcharles/srv/logs`, and `/home/samhcharles/srv/volumes` should stay reserved or be cleaned up
2. Start using `scripts/capture-vps-audit.sh` for repeatable read-only inventory snapshots
3. Write at least one additional runbook for deploy or backup recovery
4. Review and refine machine boundaries after one week of real use

## Open Questions

- Where should the long-term versioned home for this control plane live if it grows beyond the workspace root?
- Which tasks should always happen in WSL before touching the VPS?
- Which changes should require explicit approval before an agent executes them?
