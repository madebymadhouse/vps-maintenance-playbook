# Control Plane

This folder is the single source of truth for how work moves across Windows, WSL, the VPS, OpenClaw, and Discord bot repositories.

If an agent or model is about to do meaningful work, it should read this folder first instead of relying on chat history.

## Purpose

- Reduce context loss between sessions and models
- Keep machine roles explicit
- Make plans, handoffs, and runbooks reusable
- Separate verified reality from desired future changes

## First Read Order

1. `CURRENT_STATE.md`
2. `TOPOLOGY.md`
3. `WORKFLOWS.md`
4. `TEMPLATES/HANDOFF_TEMPLATE.md`
5. Relevant `RUNBOOKS/*.md`

## Working Rules

- Update `CURRENT_STATE.md` when live state changes or a major decision is made
- Update `TOPOLOGY.md` when services, repos, or ownership boundaries change
- Update `WORKFLOWS.md` when task flow changes between Windows, WSL, VPS, or agents
- Create or revise a runbook when the same operation happens more than once
- Do not leave important context only in chat

## Current Anchors

- OpenClaw framework repo: `/home/samhcharles/repos/hank-duck/openclaw`
- Discord bot runtime repo: `/home/samhcharles/srv/bots/chopsticks-lean`
- Workspace custom agent: `/home/samhcharles/.github/agents/vps-maintenance-planner.agent.md`

## Definition Of Done For Environment Work

An environment task is not done until:

1. The change is verified or the blocker is documented
2. The relevant runbook or state doc is updated
3. The next agent can understand what changed without rereading chat logs
