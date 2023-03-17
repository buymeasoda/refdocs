# Network and routing

Send request to network host to trigger response (limit count via `-c`)

    ping <domain>
    ping -c <count> <host>

Show internet route to host

    traceroute <host>

Network protocol status (limit to specific protocol `-p` eg. `tcp`, `udp`)

    netstat
    netstat -p <protocol>
