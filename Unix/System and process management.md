# System and process management

## Session

Exit the current terminal session

    exit

Restart the system

    reboot

## Processes

Kill process you own or created

    killall <process-name>

Search for named running process and return process id (`-l` to include process name)

    pgrep -l <process-name>

Kill named process (`-l` for long output, `-f` to match against full arguments)

    pkill -l <process-name>

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
