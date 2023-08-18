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

Show basic (and expanded using `any`) DNS records for domain (Note: `any` may be disabled by the DNS provider)

    dig <domain>
    dig <domain> any

Alternative DNS lookup utility to `dig`

    host -a <domain>

Show name server record type information for domain (eg. `A`, `MX`, `NS`)

    nslookup -q=<record-type> <domain>
