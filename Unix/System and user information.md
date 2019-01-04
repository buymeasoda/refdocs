# System and user information

## Session

Exit the current terminal session

    exit

Restart the system

    reboot

## Terminal

Change Unix shell (enter path to new shell when prompted)

    chsh

Output default shell

    echo $SHELL

## Maintenance

Update package list

    sudo apt-get update

Upgrade outdated packages

    sudo apt-get upgrade

## Information

Display system uptime, memory, who is logged in and what they are doing

    w

System uptime statistics

    uptime

Display your current username

    whoami

Display the machine short hostname

    hostname

Display the machine fully qualified hostname

    hostname -f

Display the Unix system type being used

    uname -a

Display real time information about process

    top

Display detailed real time information about the system

    htop

Show memory usage (in megabytes)

    free -m

Show list of running processes

    ps aux | less

Network settings including computer IP

    ifconfig

Output key / value pairs of current environment variables

    env

Output current terminal settings

    stty -a

Show distribution specific version information

    cat /etc/lsb-release

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
