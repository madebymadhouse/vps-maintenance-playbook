# Current State

Last updated: 2026-04-20

## Purpose

This repo exists so VPS maintenance does not depend on chat memory.

## Verified Facts

- The VPS is the live runtime
- The main live workload is a Discord bot stack deployed with Docker Compose
- Audit snapshots exist in `AUDITS/` and should be treated as the baseline verified inventory
- A read-only audit script exists at `scripts/capture-vps-audit.sh`
- Fresh operators should start with the docs in this folder before touching the server

## What Is Working

- The repo now has a clear first-read path for a fresh AI or human
- Topology and runtime inventory have been documented from real audit passes
- The maintenance workflow distinguishes inspection from code changes

## What Still Needs Work

- More runbooks are needed for repeated tasks such as deploy, backup, restore, and logs
- Some reserved directories and ownership boundaries are still undocumented
- Reverse proxy and scheduled maintenance are still only partially verified

## Current Operating Direction

- Use this repo as the first stop for VPS maintenance work
- Audit first when the live state is uncertain
- Write down anything the next operator would otherwise have to rediscover
- Keep repo-specific code changes in the relevant application repo, not here

## Next Practical Additions

1. Write a deploy runbook once the deploy steps are stable
2. Write a backup and restore runbook once the exact recovery flow is verified
3. Keep refreshing the topology when the live server changes
