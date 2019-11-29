# Slack

## General Search

Standard string search

    <search-string>

Combine string search with filters

    <search-string> <filter> <filter>

## Sender/Recipient Filter

Messages from sender or to recipient

    from:<username>
    to:<username>

Repeat to search across multiple users

    from:<username> from:<username> ...
    to:<username> to:<username> ...

## Channel Filter

Messages shared in a specific channel ()

    in:<channel-name>

Repeat to search across multiple channels

    in:<channel-name> in:<channel-name> ...

## Date Filter

Show messages that match date criteria (format: `yyyy-mm-dd`)

    after: <date>
    before: <date>

Combine to narrow results to specific time range

    after:<date> before:<date>
