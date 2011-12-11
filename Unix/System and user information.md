
# System and user information

Show distrubtion specific version information

	cat /etc/lsb-release

Display system uptime, memory, who is logged in and what they are doing

	w

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

Log files location

	/var/log

System uptime statistics

	uptime

Caclulate total disk usage / size for a folder

	du -sh <folder>

Show disk space usage and available space (-h makes the output human readable values)
	
	df -h
	
Find files under the root directory and below that are large than 10 MB

	find / -size +10M -printf "%s - %p\n"
