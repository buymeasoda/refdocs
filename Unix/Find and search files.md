# Find and search files

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

Search files recursively for search string below path location

    grep -R '<search-string>' <path>

## Advanced Examples

Find files with case insensitive `<search-string>` in their name

    find <path> -iname '*<search-string>*' -type f

Find files and print with sizes

    find -type f -printf '%6s %p\n'

Find files without `*.orig` and format output to include timestamp and path, then sort and grab the first 100

    find -type f -not -name '*.orig' -printf '%T+ %p\n' | sort | head -n 100

Show files with non-ascii characters

    grep -P "[\x80-\xFF]" <files>
