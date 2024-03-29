# Useful commands

## Terminal

Reload current shell in place (useful for cleanly applying recent shell config updates)

    exec $SHELL

Clear the current screen of text

    clear

## Timing

Time current command execution and output user and system timing information

    time <command>

## Prevent sleep

Prevent computer from sleeping and declare user as active

    caffeinate -u -t <seconds>

Other caffeinate options

- `-d` Prevent display sleep
- `-i` Prevent system idle sleep
- `-m` Prevent disk idle sleep

## Generate MD5 and SHA1 hashes

Generate MD5 hash from file

    md5 <file>

Generate SHA1 hash from file

    shasum <file>

## Math utilities

General maths interpreter (allows general equations entered into command line)

    bc

Calculate result of math query using `bc`

    echo <calculation> | bc
    echo '5 * 8' | bc
