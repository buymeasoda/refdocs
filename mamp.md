
# MAMP Setup on OSX

Setting up Apache, MySQL and PHP on Mac OSX. 

The guide uses the default Mac OSX Apache and PHP along with [Homebrew](http://mxcl.github.com/homebrew/) for installing MySQL.

-----------------------------------------------------------------------------

# Apache Setup

## Configure Apache

Open the Apache server configuration file `httpd.conf` for editing.

    /etc/apache2/httpd.conf

## httpd.conf settings

Set the server name to `localhost`

    ServerName localhost:80

Enable the PHP module

    LoadModule php5_module

Add index.htm to the directory index list (check if needed, php5_module may enable)

    DirectoryIndex index.html index.htm index.php

Enable the virtual hosts configuration file

    Include /private/etc/apache2/extra/httpd-vhosts.conf

## Configure virtual hosts

Location of Apache vhosts configuration file

    /etc/apache2/extra/httpd-vhosts.conf

Open `httpd-vhosts.conf` and add your vhost entries after the line

    NameVirtualHost *:80

## Apache Commands

    sudo apachectl start|stop|restart

-----------------------------------------------------------------------------

# Setup PHP

Create a php.ini file

    sudo cp /etc/php.ini.default /etc/php.ini

Paste in the contents of `php.ini-development` from the php.net distribution download

Add your timezone to date.timezone to stop PHP date warning
    
    date.timezone = "Australia/Brisbane"

Configure MySQL socket setting, find and set the following
    
    pdo_mysql.default_socket = /tmp/mysql.sock
    mysql.default_socket = /tmp/mysql.sock
    mysqli.default_socket = /tmp/mysql.sock

-----------------------------------------------------------------------------

# MySQL

## Install and configure MySQL

Install MySQL with Homebrew

    brew install mysql --with-utf8-default  
    
Follow the homebrew instructions after installation

    unset TMPDIR
    mysql_install_db
    mysql.server start
    mysql_secure_installation
    
Step through MySQL secure installation procedure

* Set a root password
* Remove anonymous user
* Disallow root login remotely
* Remove test databases
* Reload privileges

## MySQL Commands

Manage MySQL server

    mysql.server start|stop|restart|reload|force-reload|stats

`mysql.server` is a script located in: `/usr/local/Cellar/mysql/<version>/support-files`
Run with `./mysql.server <command>` or make executable

## MySQL Databases

Location of MySQL database files

    /usr/local/var/mysql

-----------------------------------------------------------------------------

# Hosts File

Open the etc hosts file

    /etc/hosts

Add entries for each virtual host (one per line)

    127.0.0.1 <your domain>

-----------------------------------------------------------------------------

# General Information

## Useful Files and Directories

Default user sites location
    
    ~/Sites

Base Apache files location

    /Library/WebServer

Default Apache page (contains default index page)

    /Library/WebServer/Documents

## Useful URLs

Open Apache manual

    http://localhost/manual/

Open user default sites folder `/User/<username>/Sites/`

    http://localhost/~<username>/
