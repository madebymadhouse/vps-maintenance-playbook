# VPS Audit Follow-Up 2026-04-19

## Scope

Second pass focused on the previously unclear paths for logs, proxy, agent staging, reserved volumes, and active network exposure.

## Verified Facts

- `/home/samhcharles/srv/agents/nqita` exists but is empty
- `/home/samhcharles/srv/logs/chopsticks` exists but is empty
- `/home/samhcharles/srv/logs/nqita` exists but is empty
- `/home/samhcharles/srv/volumes/chopsticks` exists but is empty
- `/home/samhcharles/srv/volumes/nqita` exists but is empty
- `/home/samhcharles/srv/proxy/caddy` exists but is empty
- Docker named volumes currently in use are:
  - `chopsticks-lean_postgres_data`
  - `chopsticks-lean_redis_data`
- The live bot working tree at `/home/samhcharles/srv/bots/chopsticks-lean` remained on `main` and ahead of `origin/main` by 1 commit during the follow-up audit
- The unprivileged socket snapshot showed listeners on:
  - `22` for SSH
  - `9100` for the bot health or metrics endpoint
- No listeners on `80` or `443` were observed during this pass

## Interpretation

- The `nqita`, `logs`, `volumes`, and `proxy/caddy` directories currently look like reserved structure or leftovers, not active runtime owners
- The current live persistence path for the bot stack is Docker named volumes plus the bot bind mount at `/home/samhcharles/srv/bots/chopsticks-lean/data`
- The current live host exposure is the bot health or metrics port on `9100`, not a local reverse proxy on `80` or `443`

## Remaining Unknowns

- Whether the empty directories are intentionally reserved for future expansion
- Whether any privileged services exist outside the view of an unprivileged audit
- Whether reverse proxying is expected to be restored later through another host-level path

## Recommended Follow-Up

1. Decide which empty directories are intentional and document that explicitly
2. Decide whether port `9100` should stay host-exposed or be hidden behind a future proxy or monitoring layer
3. If `nqita` is expected to become active, add a minimal README or state file to that path
