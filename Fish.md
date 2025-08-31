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

## Directory Navigation

Cycle through previous and next visited directories

    prevd
    nextd

Show the ordered directory history available to `prevd` and `nextd`

    dirh

Show numbered list of recent directories to allow jumping to specified directory

    cdh

## Private Mode

Use private mode for running commands with tokens or other context that should not be persisted to history

    fish --private
    fish -P

## String Functions

Search and replace string content (`-r` for regex)

    string replace -r <search> <replace> <input>

## Keyboard Shortcuts

### Directory Navigation

Cycle through `prevd` and `nextd` entries (when command empty)

    OPT + LEFT / RIGHT ARROW

List directory history (when current command is empty)

    ALT + D

Run `ls` for current directory

    ALT + L

### Command Completion

Show completions for current token (command, attribute or path)

    TAB

Show completions with search filter for current token

    SHIFT + TAB

Accept displayed autosuggestion

    RIGHT ARROW

Cycle through previous commands using current input

    UP / DOWN ARROW

Show searchable command history (using current command is filter)

    CTRL + R

Cycle through older and newer commands in searchable command history

    CTRL + R
    CTRL + S

### Command Editing

Clear (or halt) current command

    CTRL + C

Move the cursor to the beginning or end of the current command

    CTRL + A
    CTRL + E

Move cursor by one word within current command

    OPT + LEFT / RIGHT ARROW

Move cursor by one word (ignoring punctuation) within current command

    SHIFT + LEFT / RIGHT ARROW

Delete one character to the right of the cursor

    CTRL + D

Delete from the beginning of the line to the cursor

    CTRL + U

Delete from the cursor to the end of the command

    CTRL + U

Delete one path component

    CTRL + W

Add new line to command at current cursor position

    ALT + ENTER

### Helpers

Print short help description for command at cursor

    ALT + W

Show man page for current command

    ALT + H

Add pipe to `less` pager for current command

    ALT + P

Open file name at cursor in `less` pager

    ALT + O

Append `sudo` to current command

    ALT + S

Edit current command in external editor (set via `$VISUAL` and `$EDITOR` variables)

    ALT + E
    ALT + V

## Utilities

Output performance timings for fish shell startup

    fish --profile-startup <file> -i -c exit
