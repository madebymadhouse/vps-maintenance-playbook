# Agent Control Plane

This repo is a practical VPS maintenance notebook.

Its job is simple: a fresh AI or a tired human should be able to open this repo and understand what runs on the VPS, how to inspect it safely, and what to update after making changes.

Other developers can copy the pattern for their own server, but this repo is grounded in one real environment rather than a generic framework.

## What Is Here

- A first-read page for fresh agents and maintainers
- Current state and topology docs
- Runbooks for repeatable VPS tasks
- Audit snapshots based on verified runtime inspection
- A read-only audit script for collecting inventory

## Start Here

1. Read `control-plane/START_HERE_FOR_AGENTS.md`
2. Read `control-plane/CURRENT_STATE.md`
3. Read `control-plane/TOPOLOGY.md`
4. Read `control-plane/WORKFLOWS.md`
5. Read the relevant runbook before making changes

## Repository Layout

- `.github/agents/`
	- Optional custom agent definition for VPS maintenance work
- `control-plane/`
	- State, topology, workflows, audits, handoffs, and runbooks
- `scripts/`
	- Read-only helpers for repeatable inspection

## Scope

This repo is for:

- understanding what is running on the VPS
- keeping maintenance knowledge out of chat-only history
- making common inspection and recovery tasks repeatable
- leaving clear notes for the next operator

This repo is not for:

- application source code
- broad AI workflow theory
- product documentation

## Useful Files

- `control-plane/START_HERE_FOR_AGENTS.md`
- `control-plane/CURRENT_STATE.md`
- `control-plane/TOPOLOGY.md`
- `control-plane/RUNBOOKS/vps-audit.md`
- `scripts/capture-vps-audit.sh`

## Example Prompts

- Inspect the VPS and update the topology with verified facts only.
- Check what is running, what looks risky, and what is still undocumented.
- Read the current state and tell me the safest next maintenance step.

## License

MIT
