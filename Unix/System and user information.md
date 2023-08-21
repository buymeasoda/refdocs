# System Information

## User

Display current username (or user when using `sudo`)

    whoami
    sudo whoami

Show currently logged in user

    who

Permission details for current user

    id

List users for system

    users

Display information about system user

    finger <username>

Show login history for system (or system reboot history)

    last
    last reboot

## Operating System

Display the Unix system type being used

    uname -a

Display the processor architecture (`-p`) or machine hardware (`-m`).
(Examples: Processor `arm`, `i386` / Hardware `arm64`, `x86_64`)

    uname -p
    uname -m

Display system OS information (Linux)

    cat /etc/os-release

Show distribution specific version information (Linux)

    cat /etc/lsb-release

Display basic system OS information or more detailed system config (macOS)

    sw_vers
    system_profiler SPSoftwareDataType

## Command Info

Search system commands and display short description

    whatis <command>

Show location of command for current user path config

    which <command>

Show all locations for command

    whereis <command>

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

Local machine IP

    ipconfig getifaddr en0

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
