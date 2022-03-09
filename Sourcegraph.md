# Sourcegraph

## Shortcuts

Show search query filter list (inside search field)

    CTRL + SPACE

## Values

    <string-literal>
    <regexp-pattern>

## Declarations

Match value occurrence anywhere

    <filter>:<value>

Match results that begin or end with value

    <filter>:^<value>
    <filter>:<value>$

Find exact matches for value

    <filter>:^<value>$

Exclude results that match filter and value

    -<filter>:<value>

## Filters

Repo (exact match)

    repo:^<repo-url>$

Directory / File (with regex variations)

    file:<file-path>
    file:^<root-path>
    file:^<exact-file>$

Include or exclude results containing content string

    content:"<string>"
    -content:"<string>"

Language

    lang:<language>

## Types

Type (`diff`, `commit`, `repo`, `file`, `path`, `symbol`)

    type:diff

Author (pair with `type:diff` or `type:commit`)

    author:<name>

## Selection

Select (`repo`, `file`, `content`, `symbol`, `commit`) to define result type

    select:<type>

Example: Return list of repos that have contents which match search query

    select:repo

## Ranges

Time box results using range phrases (eg. `"1 year ago"`, `"1 week ago"`, `"1 day ago"`)

    before:<time>
    after:<time>

## Stacking

Multiple filters can be combined or regex can be used for advanced matching

    file:/common/ file:/styles.js$
    file:/common/.*/styles.js$

## Structural Search

Structural search supports multi-line and complex matchers (active via search options)

Supports using `...` "structural hole" syntax within queries

Examples

    :[[prop]]={() => :[fn]()}
    lang:JavaScript class ... extends ... {...}

## Useful Sample Queries

Show all diffs within repo during the last year for user

    repo:^<repo>$ author:<name> type:diff after:"1 year ago"
