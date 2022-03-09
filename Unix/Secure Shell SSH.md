# Secure Shell SSH

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

Add SSH key passphrase to MacOS Keychain

    ssh-add -K ~/.ssh/<key-file>

# SSH Access

Connect to remote machine using SSH public / private key instead of username and password.

On the remote machine, if there is no existing `~/.ssh` directory or `~/.ssh/authorized_keys` file, create one:

    mkdir ~/.ssh && cd ~/.ssh
    nano authorized_keys

Then past your public key into the file and save.

If an `authorized_keys` file exists, append your key to that file on a new line.
