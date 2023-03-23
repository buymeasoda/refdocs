# Slack

## Channel Notifications

Notify active members of a channel (`@here`) or all members of a channel (`@channel`)

    @here <message>
    @channel <message>

## Useful Shortcuts

Open results in split view (to keep current search results or thread in place)

    CMD + Click (message)

## General Search

Standard string search (and negated string search)

    <search-string>
    -<search-string>

Partial and wildcard matches can be formed using `*`

    <partial-string>*

Combine string search with filters

    <search-string> <filter> <filter>

## Sender/Recipient Filter

Search threads and DMs with a specific persons (or with you)

    with:<username>
    with:me

Message from or to you

    from:me
    to:me

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

Date filter vaues can be `yyyy-mm-dd` and descriptors like `today`, `yesterday` (or month names like `march` and years etc)

Show results on or during a specific date

    on:<date>
    during:<date>

Show messages that match date criteria (format: )

    after:<date>
    before:<date>

Combine to narrow results to specific time range

    after:<date> before:<date>

## Other Filters

Search only within saved items

    is:saved

Filter on messages that are pinned

    has:pin

Search messages contained within threads

    is:thread

Filter on message that have specific emoji reactions (eg. `has::dizzyblob:`) or where you have reacted with a specific emoji

    has:<emoji-code>
    hasmy:<emoji-code>
