# Working with text

## Word count

Word (`-w`), line (`-l`), character (`-m`) and byte (`-c`) count for file or piped input

    <input> | wc

## Sort

Sort lines of text in standard or reverse order (`-r`)

    <input> | sort

Sort by general numerical value

    <input> | sort -g

## Unique

Report or filter out repeated lines

    <input> | uniq

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
