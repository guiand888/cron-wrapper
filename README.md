# cron-wrapper

Generic cron script wrapper with lock file management and stale lock detection.

## Purpose

Prevents overlapping executions of cron jobs and handles stuck processes.

Follows Linux convention: place your actual scripts in `/opt` or `/usr/local/bin`, then use wrapper scripts in cron to call them. This wrapper avoids putting scripts directly in cron directories like `/etc/cron.daily`.

## Usage
1. Copy `cron-wrapper` to a new name
2. Set `TARGET_SCRIPT` to your script path
3. Configure environment variables as needed
4. `chmod +x` the wrapper
5. Call from cron or run manually

## Configuration
- `TARGET_SCRIPT` – Path to script to execute *(required)*
- `STALE_LOCK_THRESHOLD_SECONDS` – Lock timeout in seconds *(default: 3600)*

## Features
- Lock file with automatic stale detection
- Timestamp-based lock validation
- Clean exit handling
- Logging with timestamps
- Export of environment variables to target script
