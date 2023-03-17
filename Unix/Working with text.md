# Working with text

## Word count

Word (`-w`), line (`-l`), character (`-m`) and byte (`-c`) count for file or piped input

    <input> | wc

## Sort

Sort lines of text in standard or reverse order (`-r`)

    <input> | sort

Sort by numerical (`-n`) or general numerical values (`-g` handles floating points)

    <input> | sort -n
    <input> | sort -g

## Unique

Filter out repeat / duplicate lines that are adjacent (`-c` to output repeated count for each entry)

    <input> | uniq
    <input> | uniq -c

Sort lines first to position duplicate lines together for removal

    <input> | sort | uniq

Show ordered count of each repeated line (filtering out single non-repeated lines)

    <input> | uniq -c | grep -v '^ *1 ' | sort -nr

## Text replace

Pipe text into `tr` to replace content (eg. replace commas with new lines)

    <input> | tr <search> <replace>
    <input> | tr ',' '\n'

## Text extract

Output printable strings contained in file (useful for extracting metadata from binary files)

    strings <file>

## Grep

Search and output matching strings (case insensitive `-i`, display line numbers `-n`)

    grep '<search-string>' <path>
    grep -in '<search-string>' <path>

Search and output multiple matching strings

    grep '<search-string-1>\|<search-string-2>\|<search-string-3>' <path>

Pipe content into grep (eg. via `cat` or `echo`)

    cat <file> | grep '<string>'
    echo '<text>' | grep '<string>'

Show context lines after (`-A`), before (`-B`) or both sides (`-C`) of search results

    grep '<string>' -C <line-count>

## awk

Print the first (or second `$2`, third `$3` etc) field / word token for each line

    awk '{print $1}' <path>

Print lines longer the `<length>` characters (eg. 200)

    awk 'length($0) > <length>' <path>
    awk 'length($0) > 200' <path>
