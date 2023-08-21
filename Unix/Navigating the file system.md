# Navigating the file system

List files in the current directory

    ls

List filenames only one per line (numerical value `1`)

    ls -1

Long listing (`l`) of all files (`a`) with human readable sizes (`h`)

    ls -lah

List directory not the files within

    ls -d <dir>

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

## Tree

Display files and sub directories graphically

    tree

Ignore (or include) specific files and directories

    tree -I <path>
    tree -P <path>

Limit output to set folder depth (eg. 2 levels `-L 2`)

    tree -L <depth>

Other useful options

- `-a` All files (including hidden)
- `-d` List directories only
- `-f` Print full paths
- `-i` Do not indent output
- `-h` Print human readable size
- `-s` Print size in raw bytes
- `-C` Colourize output
