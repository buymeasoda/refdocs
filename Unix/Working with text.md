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

Filter out repeat lines (`-c` to output repeated count for each entry)

    <input> | uniq
    <input> | uniq -c

Show ordered count of each repeated line (filtering out single non-repeated lines)

    <input> | uniq -c | grep -v '^ *1 ' | sort -nr

## Text replace

Pipe text into `tr` to replace content (eg. replace commas with new lines)

    <input> | tr <search> <replace>
    <input> | tr ',' '\n'

# Searching text

## Grep

Search file for string (case insensitive `-i`, display line numbers `-n`)

    grep '<string>' <file>
    grep -in '<string>' <file>

Pipe content into grep (eg. via `cat` or `echo`)

    cat <file> | grep '<string>'
    echo '<text>' | grep '<string>'

Show context lines after (`-A`), before (`-B`) or both sides (`-C`) of search results

    grep '<string>' -C <line-count>
