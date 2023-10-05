# Diff

## Standard Diff

Diff files

    diff <file1> <file2>

Diff directories and their contents, showing the output of the diff for each file

    diff -r <dir1> <dir2>

Diff directories and their contents, showing only the filenames of changed files

    diff -qr <dir1> <dir2>

Diff directories ignoring specific files (eg. `.DS_Store` macOS files)

    diff -x '<ignore>' -rq <dir1> <dir2>
    diff -x '.DS_Store' -rq <dir1> <dir2>

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

# Compare

Output if specified files differ

    cmp <file1> <file2>

# Comm

Select or reject lines common to two files (requires sorted files as input)

    comm <file1> <file2>

Generates output in three columns (Disable columns using `-<column-number...>`)

- Column 1: Lines only in file 1
- Column 2: Lines only in file 2
- Column 3: Lines common in both files

Show only the common lines (eg. hide column 1 and 2 `-12` and keep column 3)

    comm -12 <file1> <file2>

Show lines only in file 1

    comm -23 <file1> <file2>

Show lines only in file 2

    comm -13 <file1> <file2>

# Sort

List lines that intersect between file 1 and file 2

    sort <file1> <file2> | uniq -d

List lines only in file one

    sort <file1> <file2> | uniq -u
