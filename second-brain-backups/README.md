# second-brain-backups

Git-versioned database backups for the Second Brain Supabase project.

Part of the [Second Brain](../README.md) ecosystem.

## What it is

A simple git repo that holds SQL dump exports. Every backup is committed so you have a full version-controlled audit trail of your database state.

## Generating a backup

Run from `second-brain-scripts/`:

```bash
npm run backup
```

Then sync to this git repo:

```bash
./src/scripts/utils/sync-backups-to-git.ps1
```

## Structure

```
backups/    # SQL dump files (timestamped)
```
