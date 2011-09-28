
# System and user information

Display system uptime, memory, who is logged in and what they are doing

	w

Display your current username

	whoami

Display the machine hostname

	hostname

Display the Unix system type being used

	uname -a
	
Display real time information about process

	top

Show list of running processes

	ps aux | less
	
Network settings including computer IP

	ifconfig

Output key / value pairs of current environment variables

	env

Caclulate total disk usage / size for a folder

	du -sh <folder>

Show disk space usage and available space (-h makes the output human readable values)
	
	df -h
	
Find files under the root directory and below that are large than 10 MB

	find / -size +10M -printf "%s - %p\n"
