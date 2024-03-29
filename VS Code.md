# VS Code

## Files

Open specific file, path or current directory in VS Code

    code <file-path>
    code .

Add file to last active editor window or new window

    code -a <file-path>
    code -n <file-path>

Open file and goto specified line

    code -g <file>:<line>

## Tools

Compare files using VS Code diff view

    code -d <file1> <file2>

## Extensions

Show list of installed extensions or list with versions

    code --list-extensions
    code --list-extensions --show-versions

## Quick Search

Open quick search panel

    CMD + P

Search for symbols (across files, in the current file, grouped by category)

    <file-name>@<symbol>
    @<symbol>
    @:<symbol>

Search for string within directory (separate string and directory by space)

    <string> <directory>

## Useful Commands

Show inlay type hints (when set to "offUnlessPressed")

    CTRL + OPTION
