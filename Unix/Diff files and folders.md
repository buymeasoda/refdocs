# Diff

## Standard Diff

Diff files

    diff <file1> <file2>

Diff directories and their contents, showing the output of the diff for each file

    diff -r <dir1> <dir2>

Diff directories and their contents, showing only the filenames of changed files

    diff -qr <dir1> <dir2>

## Vim Diff

Diff files with side by side editable output

    vim -d <file1> <file2>
    vimdiff <file1> <file2>

Pipe diff output into vim for syntax highlighting

    diff <file1> <file2> | vim -R -

## Git Diff

Compare files using the git diff tool (works outside of git repos)

    git diff --no-index <file1> <file2>

## VS Code Diff

Compare files using VS Code diff view

    code -d <file1> <file2>
