# Start Here For Agents

Read this before doing meaningful work in `/home/samhcharles`.

## Your Job

You are working in a multi-machine environment with:

- Windows as the VS Code control surface
- WSL as local Linux staging
- VPS as live runtime

Do not assume chat history is complete. Use the control plane as the durable context source.

## Required First Reads

1. `/home/samhcharles/control-plane/CURRENT_STATE.md`
2. `/home/samhcharles/control-plane/TOPOLOGY.md`
3. `/home/samhcharles/control-plane/WORKFLOWS.md`
4. `/home/samhcharles/control-plane/TEMPLATES/HANDOFF_TEMPLATE.md` if code changes are needed
5. Relevant runbook in `/home/samhcharles/control-plane/RUNBOOKS/`

## Required Questions Before Acting

1. What machine is in scope?
2. What repo or runtime service is in scope?
3. Is this planning, implementation, or maintenance?
4. What will prove success?
5. Which control-plane document must be updated afterward?

## Behavioral Rules

- Prefer verified facts over assumptions
- Do not mix planning with destructive maintenance in one leap
- Do not send coding agents into repos without a handoff contract
- If runtime facts are unclear, audit first and mark unknowns explicitly
- Leave the environment easier to understand than you found it

## Canonical Paths

- Control plane: `/home/samhcharles/control-plane`
- OpenClaw: `/home/samhcharles/repos/hank-duck/openclaw`
- Chopsticks lean: `/home/samhcharles/srv/bots/chopsticks-lean`
- Workspace custom agent: `/home/samhcharles/.github/agents/vps-maintenance-planner.agent.md`