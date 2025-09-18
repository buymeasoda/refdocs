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

Pipe command output to open in VS Code (Example: Pipe diff output of two folders)

    <command> | code -
    diff -r <folder1> <folder2> | code -

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

## Multiple Cursors

Find all matches for selection and insert cursors

    CMD + L

Find next match for selection and add cursor (repeat to create multiple cursors)

    CMD + D

Undo last cursor match insertion (repeat to undo multiple added cursors)

    CMD + U

## Useful Commands

Show inlay type hints (when set to "offUnlessPressed")

    CTRL + OPTION

## Git

Stage (or unstage) specific lines of changes inside blocks

- Open Source Control panel
- Select file from Changes list to open git diff view
- Manually select lines to stage
- Right click -> Stage Selected Ranges
