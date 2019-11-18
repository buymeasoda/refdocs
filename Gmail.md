# Gmail

## General Search

General filter across all fields using all search terms or exact phrase

    <search-string>
    "<exact-phrase>"

Exact word match `+` and removal/negation `-`

    +<search-string>
    -<search-string>

Group multiple search terms with a single filter (eg. `subject:(foo bar)`)

    <filter>:(<search-string> <search-string>)

Match multiple criteria (Alternate syntax wrap with `{}`)

    <condition> OR <condition>
    {<condition> <condition>}

Match messages where two strings are within a set distance in words (quotes to enforce order)

    <search-string> AROUND <distance> <search-string>
    "<search-string> AROUND <distance> <search-string>"

Example to match messages that contain 'foo' within 10 words of 'bar'

    foo AROUND 10 bar

## Sender/Recipient Filters

Emails from sender or to recipient

    from:<search-string>
    to:<search-string>

Extra recipient fields

    cc:<search-string>
    bcc:<search-string>

## Content and Status Filters

Subject and label fields

    subject:<search-string>
    label:<label-name>

Has or doesn't have any user labels

    has:userlabels
    has:nouserlabels

Messages based on status

    is:read
    is:unread
    is:starred
    is:snoozed
    is:important

## Location Filters

Show messages from specified location

    in:sent
    in:draft
    in:trash
    in:spam
    in:<label-name>

## Date Filters

Show emails that match date criteria (format: `yyyy/mm/dd` and other standard variations)

    after: <date>
    before: <date>

Combine to narrow results to specific time range

    after:<date> before:<date>

Show messages older or newer than a time period (`d` day, `m` month, `y` year)

    older_than:<time-period>
    newer_than:<time-period>

Examples of time period

    newer_than:2d
    older_than:3w
    newer_than:1y

## Attachment Filters

Show emails with an attachment or matching filename

    has:attachment
    filename:<file-name>

Google drive, docs and YouTube attachments

    has:drive
    has:document
    has:spreadsheet
    has:presentation
    has:youtube

## Size Filters

Show messages larger than specified size

    size: <size-bytes>

Show messages are larger or smaller than the specified sizes (combine for ranges)

    larger: <size-bytes>
    smaller: <size-bytes>
