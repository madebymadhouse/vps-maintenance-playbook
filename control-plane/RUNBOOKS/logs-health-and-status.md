# Logs, Health, And Status

Use this when you need a fast answer to: is the VPS bot healthy, and if not, where should I look first?

## Purpose

Check runtime status without guessing and without jumping straight to a restart.

## Preconditions

- You have shell access to the VPS
- You know which runtime repo is in scope

## Current Known Path

```bash
cd /home/samhcharles/srv/bots/chopsticks-lean
```

## Fast Status Checks

### Compose status

```bash
./scripts/ops/chopsticksctl.sh status
```

Or directly:

```bash
docker compose ps
```

### Bot health

```bash
./scripts/ops/chopsticksctl.sh doctor
```

Or directly:

```bash
./scripts/health-check.sh
curl -fsS http://127.0.0.1:9100/healthz
```

## Logs

### Follow bot logs

```bash
./scripts/ops/chopsticksctl.sh logs bot
```

### Follow a different service

```bash
./scripts/ops/chopsticksctl.sh logs postgres
./scripts/ops/chopsticksctl.sh logs redis
```

### Raw compose logs

```bash
docker compose logs -f --tail=200 bot
docker compose logs --tail=200 postgres
docker compose logs --tail=200 redis
```

## What To Look For

- startup failure after a deploy
- missing env or config errors
- database connection failures
- Redis connection failures
- repeated health check failures
- Discord login or REST errors

## Decision Rules

- If status is bad and health fails, inspect logs before restarting
- If health is good but commands seem stale, treat it as a command deploy problem first
- If only one service is failing, prefer a targeted fix
- If multiple core services are failing, move into incident triage instead of poking randomly

## Escalate To Incident Triage When

- the bot will not stay up
- health keeps failing after restart
- migrations may have partially run
- database state may be at risk

## What To Update Afterward

- `CURRENT_STATE.md` if the health path or logging path changed
- incident notes if the issue turned into a real outage
