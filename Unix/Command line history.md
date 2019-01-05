# Command line history

Show list of previous commands with ids (with timestamp `-f` and count limit `-100`)

    history
    history -f -100

Clear command history

    history -c

Execute command from history for history id (eg. !25, execute command 25)

    !<history-id>

Execute the last command (useful for cases like forgetting sudo, eg. `sudo !!`)

    !!
