# System Information

## User

Display current username

    whoami

Show currently logged in user

    who

Permission details for current user

    id

List users for system

    users

Show login history for system (or system reboot history)

    last
    last reboot

## Operating System

Display the Unix system type being used

    uname -a

Display system OS information (Linux)

    cat /etc/os-release

Show distribution specific version information (Linux)

    cat /etc/lsb-release

Display basic system OS information or more detailed system config (macOS)

    sw_vers
    system_profiler SPSoftwareDataType

## Command Info

Search system commands and display description

    whatis <command>

## Uptime

Display system uptime, memory, who is logged in and what they are doing

    w

System uptime statistics

    uptime

## Hostname

Display the machine short hostname

    hostname

Display the machine fully qualified hostname

    hostname -f

## Processes

Display real time information about process

    top

Display detailed real time information about the system

    htop

Show list of running processes

    ps aux | less

## Memory

Show memory usage (in megabytes)

    free -m

## Network

Network settings including computer IP

    ifconfig

## Terminal

Output key / value pairs of current environment variables

    env

Output current terminal settings

    stty -a

## Log Files

Log files location

    /var/log

## System Mail

System mail messages for users

    /var/mail/<username>

Show mail messages

    cat /var/mail/<username>

Empty mail messages (via truncate operator `>`)

    > /var/mail/<username>

Empty mail messages (alternative command)

    cat /dev/null > /var/mail/<username>
