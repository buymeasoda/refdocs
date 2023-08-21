# Network, domains and routing

Send request to network host to trigger response (limit count via `-c`)

    ping <domain>
    ping -c <count> <host>

Show internet route to host

    traceroute <host>

Network protocol status (limit to specific protocol `-p` eg. `tcp`, `udp`)

    netstat
    netstat -p <protocol>

## Domains

Show registration details for domain

    whois <domain>

## DNS Records

Show basic (and expanded using `any`) DNS records for domain (Note: `any` may be disabled by the DNS provider)

    dig <domain>
    dig <domain> any

Show specific DNS records for domain (eg. `A`, `MX`, `NS`)

    dig <record-type> <domain>

Alternative DNS lookup utility to `dig`

    host -a <domain>
    nslookup -q=<record-type> <domain>

## Name Servers

Show authoritative name servers for domain (`+short` for minimal output)

    dig NS <domain>
    dig +short NS <domain>

Alternative name server lookup utility to `dig`

    host -t NS <domain>
    nslookup -q=NS <domain>
