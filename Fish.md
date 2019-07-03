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

## Abbreviations

List full abbreviations or abbreviation names

    abbr
    abbr --list

Remove abbreviation

    abbr -e <abbr>

Rename abbreviation

    abbr -r <old-abbr> <new-abbr>

## Command History

Show all command history

    history

Clear all command history items

    history clear

Show command history that matches search string

    history search --contains <string>
    history search --prefix <string>

Remove specific entries from command history that match search string

    history delete --contains <string>
    history delete --delete <string>

Search command history from string using grep

    history | grep -i <string>
