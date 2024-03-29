# Working with files and directories

## Output file and directory information

Output filename portion of file path

    basename <path/file>

Output directory portion of file path

    dirname <path/file>

## Open and edit files

Open a file

    open <file>

Open the current directory in finder

    open .

Open a file with the specified application (Mac OSX)

    open -a /Applications/<app> <file>

Open file in the nano text editor

    nano <file>

Show line endings for files (Unix: ASCII, DOS: ASCII + CRLF)

    file <file>

## Work with remote mounts and external hard drives

Access remote mounts (such as Samba shares and external hard drives)

    cd /Volumes

## Copy, move and delete files

Copy a file (recursive copy / preserve symlinks)

    cp <source> <destination>
    cp -r <source> <destination>
    cp -a <source> <destination>

Move or rename a file

    mv <source> <destination>

Remove a file

    rm <file>

Remove files and folders recursively without confirmation

    rm -rf <dirname>

Symbolic link from source file to destination file

    ln -s <destination> <source>

## Rename files

Requires `rename` via `brew install rename`

Rename files (`-n` or `--dry-run` to test rename output with making changes)

    rename <transform> <file-glob>

Replace search string with replace string for matching files

    rename -s <search> <replace> <file-glob>

Rename all `txt` files with a sequential number in the format `text-1.txt`

    rename -e 's/.*/text-$N.txt/' *.txt
    rename -N ...01 -X -e '$_ = "text-$N"' *.txt

Uppercase first letter of zip file name (`-f` to force rename on macOS when changing case)

     rename -f 's/\b(\w)/\u$1/' *.zip

## Create and delete directories

Create directories

    mkdir <dir>
    mkdir <dir1> <dir2> <dir3>

Create multiple directories and subdirectories in one step

    mkdir -p dir1 dir2/subdir1 dir2/subdir2 dir3

Alternative syntax for multiple directories using array of items via {}

    mkdir -p dir1/{subdir1,subdir2} dir2

Multiple directory syntax can be nested

    mkdir -p tmp/{d1/{sd1,sd2},d2,d3/{sd3,sd4}}

Remove a directory

    rmdir <dirname>

## Examples of advanced file actions

Create a sequence of files from a sigle copy

    for FILE in {1..10}; do cp <file> <new-name>$FILE; done

## Create, read and output files

Output the contents of the file

    cat <file>

Join files together

    cat <file1> <file2>

Create or overwrite a file and add content via the command line (end with CTRL + d on a fresh line)

    cat > <file>

Append text via the command line to the file (end with CTRL + s)

    cat >> <file>

Overwrite the contents of the file with text

    echo "<text>" > <file>

Append the contents of file with the text

    echo "<text>" >> <file>

Create an empty file

    touch <file>
    touch <file1> <file2> <file3>

Set modified date to current time

    touch <file>

Set modified and accessed date to specific time (Time format: YYYYMMDDHHMM)

    touch -t <time> <file>
    touch -t 201001151445 <file>

Replicate modified date of source file and copy to target file

    touch -r <source> <target>

Set creation date of file (SetFile requires xcode command line tools)

    SetFile -d '<date> <time>' <file>
    SetFile -d '01/15/2010 14:45:00' <file>

## File Status

Output status information for file (use `-f` for selective metadata and output format)

    stat <file>

Output file size followed by the file name

    stat -f "%z %N" <file>

## Tail and Head

Display the first or last part of a file

    head
    tail

## Less and More

Paginate through a text file output directly in the terminal

    more <filename>

Paginate through a text files output directly in the terminal (includes ability to go backwards)

    less <filename>

## Less commands

Go to end of file

    >

Go to end of file

    <

Back one page

    b

Forward one page

    f
