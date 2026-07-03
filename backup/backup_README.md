# backup

A Bash script that automates backing up recently modified files from a project directory into a timestamped `.tar.gz` archive, with automatic cleanup of old backups.

## Overview

This script was built to remove the manual effort of tracking and archiving recently changed files. It runs a simple check-archive-clean cycle each time it's executed, making it suitable for periodic use via cron or manual runs.

## What It Does

1. Verifies the source directory exists before doing anything
2. Finds all files modified within the last 24 hours
3. Archives them into a timestamped `.tar.gz` file
4. Moves the archive into a dedicated backup directory
5. Deletes any backup archives older than 7 days

## Usage

```bash
backup
```

If the script's directory has been added to your `$PATH`, it can be run from anywhere. Otherwise, run it directly:

```bash
./backup
```

## Configuration

Set these variables at the top of the script to customize its behavior:

| Variable | Description | Default |
|---|---|---|
| `project` | Name of the directory to back up (relative to `$HOME`) | `project` |
| `backupDestination` | Where backup archives are stored | `~/backup` |
| `backupFileName` | Naming pattern for each archive | `backup_YYYY-MM-DD_HH-MM-SS.tar.gz` |

## Output

Backups are saved to:

```
~/backup/backup_<date>_<time>.tar.gz
```

## Requirements

- Bash
- Standard Unix utilities: `find`, `tar`, `mv`, `date`

## Automating with Cron

To run this automatically, for example every day at midnight, add the following to your crontab:

```bash
crontab -e
```

```
0 0 * * * /path/to/backup
```

## Notes

- Only files modified in the last 24 hours are included in each run, so this script is intended to be run at least once daily to avoid missing changes.
- Old backups are automatically removed after 7 days to prevent unbounded disk usage. Adjust the `-mtime +7` value in the script if a longer or shorter retention period is needed.

## Example

```bash
$ backup
```

```
~/backup/backup_2026-07-04_09-15-32.tar.gz
```

## License

This script is part of the [bash-scripts](../) collection and is licensed under the MIT License.
