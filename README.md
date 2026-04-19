# Agent Control Plane

An open-source control plane for agentic development across Windows, WSL, and a Linux VPS.

The point of this repo is simple: stop losing environment context between chats, models, and machines.

## What This Repo Gives You

- A custom VS Code agent at `.github/agents/vps-maintenance-planner.agent.md`
- A control-plane document set under `control-plane/`
- A repeatable VPS audit workflow
- A read-only snapshot script for collecting runtime inventory

## Quick Start

1. Read `control-plane/START_HERE_FOR_AGENTS.md`
2. Read `control-plane/CURRENT_STATE.md`
3. Read `control-plane/TOPOLOGY.md`
4. Read `control-plane/WORKFLOWS.md`
5. Use `control-plane/HANDOFFS/` before asking a coding agent to mutate a repo

## Repository Layout

- `.github/agents/`
	- Custom agent definitions for VS Code
- `control-plane/`
	- Current state, topology, workflows, handoffs, audits, and runbooks
- `scripts/`
	- Read-only helper scripts for repeatable environment inspection

## Why This Exists

Most agent workflows degrade because:

- planning stays in chat instead of docs
- runtime facts are mixed with guesses
- coding agents are sent into repos without a contract
- Windows, WSL, and VPS responsibilities are never written down

This repo fixes that by making the environment explicit.

## Current Scope

This version is optimized for:

- OpenClaw-oriented agent orchestration
- Discord bot hosting on a VPS
- separating planning from implementation
- documenting real runtime inventory before maintenance work

## Useful Files

- `control-plane/TOPOLOGY.md`
- `control-plane/CURRENT_STATE.md`
- `control-plane/RUNBOOKS/vps-audit.md`
- `control-plane/HANDOFFS/2026-04-19-topology-inventory-automation.md`
- `scripts/capture-vps-audit.sh`

## Example Prompts

- Map my current VPS runtime and update the topology with verified facts only.
- Write a handoff for a coding agent to change deployment behavior safely.
- Run the VPS audit workflow and tell me what is real versus undocumented.

## License

MIT
