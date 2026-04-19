# Agent Control Plane

An open-source control plane for running agentic development across Windows, WSL, and a Linux VPS without losing context between sessions.

## What This Repo Contains

- A custom VS Code agent at `.github/agents/vps-maintenance-planner.agent.md`
- Control-plane documents for topology, current state, workflows, handoffs, audits, and runbooks under `control-plane/`

## Why This Exists

Most agent workflows fail because planning, runtime facts, and coding work are mixed together in chat history.

This repo makes the environment itself explicit:

- where work should happen
- which machine owns which task
- how to hand work off to coding agents
- how to audit the VPS without guessing
- what needs to be updated after each meaningful change

## Intended Use

1. Read `control-plane/START_HERE_FOR_AGENTS.md`
2. Read `control-plane/CURRENT_STATE.md`
3. Read `control-plane/TOPOLOGY.md`
4. Read `control-plane/WORKFLOWS.md`
5. Use a handoff from `control-plane/HANDOFFS/` before delegating implementation work

## Current Focus

This initial version is built around:

- OpenClaw-oriented agent workflows
- Discord bot hosting on a VPS
- separating planning from implementation
- reducing context drift across models and machines

## License

MIT
