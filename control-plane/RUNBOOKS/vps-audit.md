# VPS Audit

## Purpose

Create a repeatable way to inspect the VPS without mixing observation with changes.

## Preconditions

- SSH or terminal access is available
- You know whether the goal is inventory, diagnosis, or pre-maintenance review

## Audit Categories

1. Services
2. Containers
3. Repos and deploy paths
4. Logs
5. Scheduled jobs
6. Backups
7. Reverse proxy and exposed ports

## Checklist

### Services

- List active systemd services relevant to bots, agents, proxy, or databases
- Record service names, purpose, and restart ownership

### Containers

- Identify active Docker containers or compose projects
- Record which paths own each stack

### Repos And Paths

- Record runtime repo paths under `/srv` and any linked working copies
- Note whether each repo is edited in place or deployed from elsewhere

### Logs

- Identify primary log locations under `/home/samhcharles/logs` and service-specific paths
- Record how to inspect recent failures quickly

### Scheduled Jobs

- Record cron jobs, timers, backup scripts, and health checks

### Backup State

- Record backup scripts, destinations, and latest successful checkpoint if known

### Proxy And Network

- Record proxy location and domain routing ownership
- Note exposed ports and which service owns them

## Output Format

For each audit session, capture:

- Verified facts
- Unknowns
- Risks
- Recommended cleanup or documentation work

## Verification

The audit is complete when `TOPOLOGY.md` or a dedicated runbook is updated with the findings.

## Failure Handling

- If a category cannot be verified, mark it unknown instead of guessing
- If you find drift between docs and reality, document both and prefer verified runtime facts