# Sync Files

## Usage

    rsync <options> <source> <destination>

## Backup Mode

Perform a mirrored one way sync of source files to destination, removing deleted files from destination (Archive mode flag `-a` is the same as `-rlptgoD`)

    rsync -avhP --stats --delete <source> <destination>

## Archive Mode

Perform a mirrored one way sync, deleting destination files but retain a destination backup of deleted files in a date stamped folder

    rsync -avhP --stats --delete --backup --backup-dir="backup_$(date +\%Y-\%m-\%d)" <source> <destination>

## Common Flags

Flags encompassed by archive mode

- `-r` recurse into subdirectories
- `-l` copy symlinks as symlinks
- `-p` preserve permissions
- `-t` preserve timestamp
- `-g` preserve group
- `-o` preserve owner
- `-D` preserve device and special files

To opt out of an archive mode default flag

- `--no-<option>` (eg. `--no-D` to disable `-D`)

## Dry Run

- `-n` dry run what will be transferred

## Display Flags

- `-v` verbose output
- `-h` human readable output
- `-P` show progress and keep partial files

## Transfer Flags

- `-u` skip files that are newer on the receiver
- `-z` compress data during transfer
- `--delete` delete extraneous files from destination dirs
- `--exclude=<pattern>` exclude files matching `<pattern>`
