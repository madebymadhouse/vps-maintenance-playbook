# Docker Deploy And Verify

Use this when updating a VPS-hosted bot that runs under Docker Compose.

This runbook is based on the actual `chopsticks-lean` VPS flow and the stronger operational patterns used in the full `madebymadhouse/chopsticks` repo.

## Purpose

Pull the latest code, restart only what is needed, verify health, and avoid turning a small deploy into a blind reboot.

## Preconditions

- You know which repo on the VPS is in scope
- Docker and Docker Compose are available
- The correct `.env` is already present
- You know whether migrations or command deployment are part of the change

## Current Known Path

The verified live bot path in this environment is:

```bash
cd /home/samhcharles/srv/bots/chopsticks-lean
```

The current compose stack includes:

- `chopsticks-lean-bot`
- `chopsticks-lean-postgres`
- `chopsticks-lean-redis`

## Preferred Entry Point

Use the repo's control script instead of improvising individual commands when possible.

```bash
./scripts/ops/chopsticksctl.sh up
```

That path already does useful preflight work:

- validates deployment assumptions
- starts the compose stack
- waits for bot readiness
- checks bot health
- runs migrations
- optionally deploys commands

## Safe Update Flow

### 1. Review current state

```bash
./scripts/ops/chopsticksctl.sh status
./scripts/ops/chopsticksctl.sh doctor
```

### 2. Pull the latest code

```bash
git pull origin main
```

### 3. Apply the update

If the normal one-click path is wanted:

```bash
./scripts/ops/chopsticksctl.sh up
```

If you need tighter control:

```bash
docker compose up -d --build
./scripts/ops/chopsticksctl.sh migrate
```

### 4. Deploy commands if command files changed

Use guild mode first unless there is a clear reason to go global.

```bash
./scripts/ops/chopsticksctl.sh deploy guild
```

## Verification

Minimum verification after the deploy:

```bash
./scripts/ops/chopsticksctl.sh status
./scripts/ops/chopsticksctl.sh doctor
./scripts/health-check.sh
```

Direct health check:

```bash
curl -fsS http://127.0.0.1:9100/healthz
```

If behavior changed in Discord, verify one real command in the target guild.

## Failure Handling

- If `doctor` fails, inspect bot logs before rebuilding again
- If migrations fail, stop and resolve schema issues before retrying
- If the bot is healthy but commands are stale, redeploy commands instead of restarting the whole stack
- If only one service looks broken, prefer a targeted restart over taking down Postgres and Redis unnecessarily

## What To Update Afterward

- `CURRENT_STATE.md` if the operational path changed
- `TOPOLOGY.md` if service layout, ports, paths, or ownership changed
- this runbook if the deploy process itself changed
