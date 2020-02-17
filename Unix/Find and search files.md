# Find and search files

## Find

Find allows searching file names and directories under the current location

    find <path> <settings>

Show files that match the search criteria. The criteria can be a literal name or use wildcards `*`
Wrap non-alphanumeric search criteria with quotes

    find . -name '<file-pattern>'

Find files (`-type f`), directories (`-type d`) or both

    find <path> -type f
    find <path> -type d
    find <path>

Find files that match the file pattern and pass results to grep for searching file contents

    find <path> -name '<file-pattern>' | xargs grep '<search-string>'

Find folders that are at a certain depth with the specified name

    find . -mindepth 1 -maxdepth 1 -type d -name '<search-string>'

Find files containing case insensitive `<search-string>` somewhere in their name

    find <path> -iname '*<search-string>*' -type f

## Grep

Output files with content matching (`-l`) or not matching (`-L`) the search string

    grep -l '<search-string>' <path>
    grep -L '<search-string>' <path>

Search files recursively for search string below path location

    grep -R '<search-string>' <path>

Search using extended regex (`-E`)

    grep -E '<extended-regex>' <path>

Only show matches (`-o`) and do not print filenames (`-h`)

    grep -ho '<search-string>' <path>

## Advanced Examples

Find files and print with sizes (Note: `-printf` is not POSIX and only available with GNU `find`)

    find . -type f -printf '%6s %p\n'

Find files without `*.orig` and format output to include timestamp and path, then sort and grab the first 100

    find . -type f -not -name '*.orig' -printf '%T+ %p\n' | sort | head -n 100

Show files with non-ascii characters

    grep -P "[\x80-\xFF]" <files>

List all image filenames

    ls | grep -iE ".*\.(gif|jpe?g|png|svg)"
