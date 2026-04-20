# Backup And Restore

Use this when backing up or restoring the VPS bot database.

This runbook is based on the real scripts in `samhcharles/chopsticks-lean`.

## Purpose

Handle database backup and restore carefully enough that a fresh operator does not destroy data by rushing.

## Preconditions

- You are in the correct bot repo
- The Postgres container is running
- You understand that restore is destructive

## Current Known Path

```bash
cd /home/samhcharles/srv/bots/chopsticks-lean
```

## Backup

### Default backup path

The verified default backup path is the repo-local data folder unless overridden:

```bash
./data/backups
```

### Run a backup

```bash
./scripts/backup-db.sh
```

Optional explicit output directory:

```bash
./scripts/backup-db.sh /home/samhcharles/srv/backups/manual
```

The script:

- dumps PostgreSQL from the compose container
- writes a timestamped `.sql.gz`
- prunes old backups based on `BACKUP_KEEP_DAYS`

### Verify backup output

```bash
ls -lh ./data/backups
ls -lh /home/samhcharles/srv/backups/manual
```

## Restore

### Warning

Restore is destructive. The current restore script drops and recreates the database before loading the selected dump.

Do not run restore as a casual troubleshooting step.

### Show available backups

```bash
ls -lh ./data/backups/*.sql.gz
```

### Run restore

```bash
./scripts/restore-db.sh ./data/backups/<backup-file>.sql.gz
```

The script will ask for explicit confirmation by requiring `YES`.

## After Restore

Run health and status checks immediately:

```bash
./scripts/ops/chopsticksctl.sh status
./scripts/ops/chopsticksctl.sh doctor
```

If command or data behavior matters, verify the affected workflows in Discord.

## Failure Handling

- If backup fails, check that the Postgres container is running and named correctly
- If restore fails mid-stream, stop and assess database state before retrying
- If restore succeeds but app behavior is wrong, inspect migrations and app logs before doing more damage

## What To Update Afterward

- `CURRENT_STATE.md` if backup ownership or storage location changed
- incident notes if a restore was part of outage recovery
- this runbook if the scripts or backup paths change
