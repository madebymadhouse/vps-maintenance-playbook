# VPS Docs

This folder is the working memory for the VPS.

If an agent or human is about to inspect, change, or recover something on the server, they should read this folder first instead of relying on chat history.

## First Read Order

1. `CURRENT_STATE.md`
2. `TOPOLOGY.md`
3. `WORKFLOWS.md`
4. Relevant `RUNBOOKS/*.md`
5. `TEMPLATES/HANDOFF_TEMPLATE.md` if code changes are needed

## What Belongs Here

- what is running now
- what has been verified
- what is risky, broken, or still unknown
- how to perform repeatable VPS tasks safely
- what changed during the last maintenance pass

## Current Runbooks

- `RUNBOOKS/vps-audit.md`
- `RUNBOOKS/docker-deploy-and-verify.md`
- `RUNBOOKS/logs-health-and-status.md`
- `RUNBOOKS/backup-and-restore.md`
- `RUNBOOKS/incident-triage.md`

## Working Rules

- Update `CURRENT_STATE.md` when the live state changes or a maintenance decision matters later
- Update `TOPOLOGY.md` when services, paths, ports, or ownership boundaries change
- Add or revise a runbook when the same task happens more than once
- Keep verified facts separate from guesses or future ideas
- Do not leave important maintenance context only in chat

## Done Means

A VPS task is not done until:

1. The change is verified or the blocker is written down
2. The relevant doc or runbook is updated
3. The next operator can understand what changed without rereading chat logs
