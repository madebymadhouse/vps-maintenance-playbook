# Incident Triage

Use this when the VPS bot is down, unhealthy, or acting wrong after a deploy.

## Purpose

Get from vague breakage to a controlled next step without flailing.

## First Questions

1. Is the bot down, unhealthy, or just missing commands?
2. Did a deploy, migration, or env change happen recently?
3. Are PostgreSQL and Redis healthy?
4. Is the issue local to Discord interactions or broader runtime health?

## Fast Triage Order

### 1. Check runtime status

```bash
cd /home/samhcharles/srv/bots/chopsticks-lean
./scripts/ops/chopsticksctl.sh status
```

### 2. Check health

```bash
./scripts/ops/chopsticksctl.sh doctor
./scripts/health-check.sh
```

### 3. Check logs

```bash
./scripts/ops/chopsticksctl.sh logs bot
```

If needed:

```bash
docker compose logs --tail=200 postgres
docker compose logs --tail=200 redis
```

### 4. Separate runtime failure from command failure

If the bot is healthy but Discord interactions look stale:

```bash
./scripts/ops/chopsticksctl.sh deploy guild
```

Do not restart the whole stack first if command registration is the real problem.

## Smallest Valid Recovery

Start with the least destructive step that matches the failure.

Examples:

- rerun command deployment
- restart only the bot container
- rerun migrations if startup failed after schema changes
- restore from backup only when data integrity is the real problem

## When To Escalate

Escalate the incident when:

- health still fails after targeted recovery
- multiple services are down
- migrations may have partially applied
- restore may be required
- the next step could make data loss worse

## What To Record

After the incident, write down:

- what failed
- what was checked first
- what fixed it or did not fix it
- what still feels risky
- which doc or runbook needs to improve

## What To Update Afterward

- `CURRENT_STATE.md` if operational reality changed
- `TOPOLOGY.md` if runtime structure changed
- this runbook if the incident exposed a weak maintenance path
