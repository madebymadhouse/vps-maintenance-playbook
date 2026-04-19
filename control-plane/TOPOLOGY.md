# Topology

## Machine Roles

### Windows

- Primary VS Code user interface
- Main place where chat-driven planning and review happen
- Should be treated as the human control surface, not the authoritative runtime

### WSL

- Linux-compatible local staging environment
- Good place for script development, validation, and dry runs
- Best place to test automation that will later run on the VPS

### VPS

- Live runtime for bots, services, logs, and operations
- Should be treated as production or production-like state
- Changes here should follow runbooks and leave documentation behind

## Known Repos And Paths

### OpenClaw

- Path: `/home/samhcharles/repos/hank-duck/openclaw`
- Role: agent framework and coder orchestration contract
- Important docs:
  - `workspace-coder/AGENTS.md`
  - `workspace-coder/SOUL.md`
  - `workspace-coder/MEMORY.md`

### Chopsticks Lean

- Path: `/home/samhcharles/srv/bots/chopsticks-lean`
- Role: Discord bot runtime and deployment target
- Deploy model: live Git working tree on the VPS with Docker Compose runtime
- Git remote: `https://github.com/samhcharles/chopsticks-lean`
- Branch state during audit: `main` ahead of `origin/main` by 1 commit
- Important docs:
  - `README.md`
  - `DEPLOYMENT.md`
  - `migrations/README.md`

## Verified Runtime Inventory

### Docker Stack

- Active runtime is a Docker Compose stack defined at `/home/samhcharles/srv/bots/chopsticks-lean/docker-compose.yml`
- Running containers observed during audit:
  - `chopsticks-lean-bot`
  - `chopsticks-lean-postgres`
  - `chopsticks-lean-redis`
- Bot health endpoint is exposed on host port `9100`
- Bot container bind-mounts `/home/samhcharles/srv/bots/chopsticks-lean/data` to `/app/data`
- Postgres and Redis persistence use Docker named volumes declared in Compose

### Systemd

- No enabled or currently running custom systemd services matching `chopsticks`, `nqita`, `caddy`, `postgres`, `redis`, or `docker` were observed from the unprivileged audit filters
- A systemd service example exists at `/home/samhcharles/srv/bots/chopsticks-lean/systemd/chopsticks-lean.service.example`, but the live runtime currently appears to be Compose-driven rather than systemd-driven

### Runtime Paths

- Service root: `/home/samhcharles/srv`
- Bots root: `/home/samhcharles/srv/bots`
- Agent root: `/home/samhcharles/srv/agents`
- Backups root: `/home/samhcharles/srv/backups`
- Logs root: `/home/samhcharles/srv/logs`
- Proxy root: `/home/samhcharles/srv/proxy`
- Volumes root: `/home/samhcharles/srv/volumes`

### Known Live Directories

- Bot directories observed:
  - `/home/samhcharles/srv/bots/chopsticks`
  - `/home/samhcharles/srv/bots/chopsticks-lean`
- Agent directories observed:
  - `/home/samhcharles/srv/agents/nqita`
- Volume directories observed:
  - `/home/samhcharles/srv/volumes/chopsticks`
  - `/home/samhcharles/srv/volumes/nqita`

## Backups And Restore

- Verified shared backup root: `/home/samhcharles/srv/backups`
- Verified manual backup subdirectory: `/home/samhcharles/srv/backups/manual`
- Chopsticks lean backup script exists at `/home/samhcharles/srv/bots/chopsticks-lean/scripts/backup-db.sh`
- Chopsticks lean restore script exists at `/home/samhcharles/srv/bots/chopsticks-lean/scripts/restore-db.sh`
- Chopsticks lean database backups default to `./data/backups` relative to the repo unless `BACKUP_DIR` overrides that path
- No user crontab entries were present during the audit, so automated database backup scheduling is not yet verified from this pass

## Proxy And Routing

- Proxy path exists at `/home/samhcharles/srv/proxy/caddy`
- No Caddy config files were present in that directory during the audit
- Reverse proxy ownership and active domain routing remain unverified

## Scheduling

- No user crontab entries were present during the audit
- Only standard system timers were observed in the initial timer pass
- No custom backup or deploy timer has been verified yet

## Responsibility Boundaries

- Control-plane reasoning belongs in `/home/samhcharles/control-plane`
- Repo-specific coding belongs inside the relevant repo
- Runtime state belongs on the VPS, but the explanation of that state belongs in the control plane

## Agent Trust Boundaries

- `VPS Maintenance Planner` should be used for topology, workflow, maintenance planning, and documentation updates
- Coding-focused agents should receive a written handoff before making repo changes
- Live runtime inspection should precede any maintenance change when the current state is uncertain

## Remaining Unknowns

These still need to be documented explicitly or verified in a deeper audit:

- Whether any privileged systemd units exist outside the unprivileged audit view
- What domains, TLS setup, and upstream routes are currently intended for Caddy or another proxy layer
- Whether `/home/samhcharles/srv/agents/nqita` is runtime-active or only staged
- Whether `/home/samhcharles/srv/volumes/chopsticks` and `/home/samhcharles/srv/volumes/nqita` are current sources of truth or remnants from older layouts
- Which tasks must always be staged in WSL before touching the VPS
