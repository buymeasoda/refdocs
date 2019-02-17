# System and process management

## Session

Exit the current terminal session

    exit

Restart the system

    reboot

## Processes

Kill process you own or created

    killall <process-name>

Search to see if a process is running (returns process id)

    pgrep -l <process-name>

Search for process details

    ps aux | grep <process-name>

Kill a running process (by id)

    kill <process-id>
    sudo kill <process-id>

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
