# Disk usage and file sizes

Calculate total disk usage / size for a folder

    du -sh <folder>

Ignore specified files and directories when calculating size

    du -sh -I <ignore-pattern> <folder>

Show disk space usage and available space (-h makes the output human readable values)

    df -h

## Usage Examples

Find files under the root directory and below that are larger than 10 MB (optionally ignore `.git` directories)

    find <path> -size +10M
    find <path> -size +10M -not -path '*/\.git/*'

Format output when using GNU `find` (Note: `-printf` is not POSIX)

    find <path> -size +10M -printf "%s - %p\n"

Show ten largest files and directories under current location

    du . | sort -nr | head -n10
    du -s * | sort -nr | head -n10

Calculate size of files in git repo (ignoring git directory)

    du -sh -I .git <folder>
