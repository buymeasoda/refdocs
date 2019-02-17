# User, file and group permissions

## Sudo

Perform a command as the super user

    sudo <command>

## Switch users

Switch to specific user

    su <user>

Switch to root or specific user and load user profile (`CTRL + d` to exit user mode)

    su -
    su - <user>

## Managing users

Create a new user

    adduser <username>

Change password for active user

    passwd

## File permissions

Change file mode and access control

    chmod <permissions> <file>

Permission types

    r = read
    w = write
    x = execute

Numerical values

    r = 4
    w = 2
    x = 1

Permission groups

    u = user
    g = group
    o = other
    a = all (sets u, g and o)

### Set permissions with assigment

Set user to rwx, group to rw and other to r

    chmod u=rwx,g=rw,o=r <file>

Set u to rwx, group and other to r

    chmod u=rwx,go=r <file>

### Alter some permission with plus and minus

Add write permissions to user group

    chmod g+w <file>

Remove read and write permission from other group

    chmod o-rw <file>

Add execute for user, remove write for group, remove rwx for other

    chmod u+x,g-w,o-rwx

### Use -R to set permissions recursively

Set group to read and write for the directory and all sub files and folders

    chmod -R g=rw <dir>

## Managing groups and owners

List available groups

    less /etc/group

Modify a user (usermod) and add (-a) them to a group (-G)

    usermod -a -G <group> <username>

Change file group associated with the file permissions

    chgrp <group> <file>

Change file owner

    chown <user> <file>

## Cleaning up file permissions

Find files with permission set to 777 and change them to default 644

    find . -type f -perm 777 -print0 | xargs -0 chmod 644

Find directories with permission set to 777 and change them to default 755

    find . -type d -perm 777 -print0 | xargs -0 chmod 755

Unlock all locked files found under the current directory

    chflags -R nouchg *
