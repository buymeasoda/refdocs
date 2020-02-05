# Navigating the file system

List files in the current directory

    ls

List filenames only one per line (numerical value `1`)

    ls -1

Long listing (`l`) of all files (`a`) with human readable sizes (`h`)

    ls -lah

Reverse sort order

    ls -r

Recursively list subdirectories

    ls -R

Useful sort order flags

- Modified time `-t`
- Last accessed time `-u`
- Creation time `-U`
- File size `-S`

Change directory

    cd <dir>

Go to home directory

    cd ~

Go to system root directory

    cd /

Return to last directory

    cd -

Show the path of the current directory location (print working directory)

    pwd

Display files and sub directories graphically

    tree

List files via tree with full paths (`-f`), no indents (`-i`) and unescaped characters (`-N`)

    tree -ifN
