# Disk usage and file sizes

Calculate total disk usage / size for a folder

    du -sh <folder>

Show disk space usage and available space (-h makes the output human readable values)

    df -h

Find files under the root directory and below that are large than 10 MB

    find / -size +10M -printf "%s - %p\n"

Show ten largest files and directories under current location

    du . | sort -nr | head -n10
    du -s * | sort -nr | head -n10
