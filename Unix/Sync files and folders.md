# Sync Files

## Usage

    rsync <options> <source> <destination>

## Archive Mode

Perform mirrored archive (deleting remote files that no longer exist locally), showing verbose, human readable output and progress.

    rsync -avhP --delete <source> <destination>

Archive mode flag

- `-a` archive mode (same as `-rlptgoD`)

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
