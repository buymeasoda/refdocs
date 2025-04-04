# Fish

## Install

Install fish via homebrew

    brew install fish

Set fish as default shell

    echo /usr/local/bin/fish | sudo tee -a /etc/shells
    sudo chsh -s $(which fish) $(whoami)

Default fish config folder location

    ~/.config/fish

## Completions

Update man page completions

    fish_update_completions

## Functions

List available fish functions

    functions

Show source for specific function (`type` provides syntax highlighting)

    functions <function-name>

List Builtin function names

    builtin --names

## Environment

Set environment variable for command

    env <variable>=<value> <command>

## Abbreviations

Add (`-a`) global (`-g`) abbreviation

    abbr -ag gc 'git ci -m'

Add (`-a`) global (`-g`) abbreviation and set cursor position

    abbr -ag gc --set-cursor=@ 'git ci -m "@"'

List full abbreviations or abbreviation names

    abbr
    abbr --list

Remove abbreviation

    abbr -e <abbr>

Rename abbreviation

    abbr -r <old-abbr> <new-abbr>

## Command History

Show all command history items

    history

Clear all command history items

    history clear

Limit history results (show `count` most recent entries, eg. `-5` five entries)

    history -<count>
    history -5

Include timestamp of command in history output

    --show-time -t

Show history matching filter and string criteria (optionally limit to `-n` results)

    history search <filter> <string>
    history search <filter> <string> -n <count>

Delete history matching filter and string criteria

    history delete <filter> <string>

History result filters

    --exact -e
    --prefix -p
    --contains -c

Set filter string to be case sensitive

    --case-sensitive -C

List history entries that contain the specified string

    history search --contains <string>

Delete history entries that contain the specified string

    history delete --contains <string>

Search command history from string using grep

    history | grep -i <string>

## Private Mode

Use private mode for running commands with tokens or other context that should not be persisted to history

    fish --private
    fish -P

## String Functions

Search and replace string content (`-r` for regex)

    string replace -r <search> <replace> <input>
