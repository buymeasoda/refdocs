
# Secure FTP (SFTP) and Secure Copy (SCP)

## SFTP

Connect to remote server using sftp (add `-oPort=<port>` if port is required)

	sftp <user>@<host>

A subset of standard unix commands are available while connected.

Upload a file

	put <local> <remote>

Download a file

	get <remote> <local>

Quit sftp
	
	bye

	exit


## SCP

Secure copy files to or from remote server

	scp <source> <destination>

For destination, specify the remote server, then remote path/file separated by a colon

	<user>@<host>:<path/file>

Specify local file using local system path. Use a single dot to indicate current directory. Use lowercase r for recursive copy.

### SCP Examples

Copy a remote file on server user@host, located at path/file, to the local path

	scp <user>@<host>:<path/file> <local path>
		
Copy a local file at path/file to another remote server

	scp <local path/file> <user>@<host>:<path>
		
Recursively copy the files and folders from local dir to the remote server home directory

	scp -r <local dir> <user>@<host>:~
