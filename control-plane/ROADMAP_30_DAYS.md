# 30 Day Roadmap

## Week 1

Goal: establish control-plane habits and stop starting blind.

1. Use `control-plane/README.md` as the first read before agent work
2. Use the `VPS Maintenance Planner` agent for planning and environment questions
3. Fill in missing inventory in `TOPOLOGY.md`
4. Write one real handoff before asking a coding agent to change a repo

Success condition:
- at least one task is completed with plan, handoff, verification, and state update

## Week 2

Goal: make repeated operations explicit.

1. Write runbooks for deploy, backup, and service restart flows
2. Document which machine owns each recurring task
3. Identify any path, env, or service naming inconsistencies

Success condition:
- two recurring operations no longer depend on memory or chat logs

## Week 3

Goal: tighten agent boundaries.

1. Separate planning prompts from implementation prompts
2. Decide which agents are allowed to mutate VPS state
3. Add at least one repo-specific handoff template if needed

Success condition:
- less time spent re-explaining repo structure and environment role boundaries

## Week 4

Goal: review drift and stabilize.

1. Review what docs stayed current and what did not
2. Remove redundant notes or stale plans
3. Promote the control plane into a dedicated repo if it proves useful

Success condition:
- the control plane is trusted enough to become the default first-read context
