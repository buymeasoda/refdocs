
# Secure Shell (SSH)

Connect as <user> to remote <host> on specified <port>
If you do not specify a username it uses your current username

	ssh -p <port> <user>@<host>

## SSH Config

Location of SSH settings and host configuration

	~/.ssh

If an SSH config file (or the ssh directory) doesn't exist create it at:

	~/.ssh/config

Add details for a host entry

	Host <nickname>
	 
	    HostName <server>
	    User <username>
	    Port <port>

Use SSH configuration

	ssh <nickname>