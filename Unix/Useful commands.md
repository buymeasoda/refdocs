# Useful commands

## Terminal

Clear the current screen of text

    clear

## History

Show list of previous commands with ids (with timestamp `-f` and count limit `-100`)

    history
    history -f -100

Clear command history

    history -c

Execute command from history for history id (eg. !25, execute command 25)

    !<history-id>

Execute the last command (useful for cases like forgetting sudo, eg. `sudo !!`)

    !!

## Generate MD5 and SHA1 hashes

Generate MD5 hash from file

    md5 <file>

Generate SHA1 hash from file

    shasum <file>

## Other Utilities

Word, line, character and byte count for file or piped input

    wc

General maths interpreter (allows general equations entered into command line)

    bc

Show line endings for files (Unix: ASCII, DOS: ASCII + CRLF)

    file <file>

Sort lines of text

    sort

Report or filter out repeated lines

    uniq
