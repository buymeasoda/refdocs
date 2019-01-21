# MAMP Setup on OSX

Setting up macOS with Apache, MySQL and PHP.

The guide uses the default Mac OSX Apache and PHP along with [Homebrew](http://mxcl.github.com/homebrew/) for installing MySQL.

# Apache

Open the Apache server configuration file `httpd.conf` for editing

    /private/etc/apache2/httpd.conf

## httpd.conf settings

Set the server name to `localhost`

    ServerName localhost:80

Configure document root for sites folder (create `~/Sites` if needed)

    DocumentRoot "/Users/<user-name>/Sites"
    <Directory "/Users/<user-name>/Sites">

Set log file location and create folder if needed

    ErrorLog "/private/var/log/apache2/error_log"
    CustomLog "/private/var/log/apache2/access_log" common

Enable the PHP module (add or uncomment)

    LoadModule php7_module libexec/apache2/libphp7.so

Expand directory index file extensions (not required when `other/php7.conf` is used)

    DirectoryIndex index.html index.htm index.php

Enable the virtual hosts configuration file (add or uncomment)

    Include /private/etc/apache2/extra/httpd-vhosts.conf

## Virtual hosts

Edit Apache vhosts configuration file

    /private/etc/apache2/extra/httpd-vhosts.conf

Remove sample configs and add new vhost

    <VirtualHost *:80>
    	DocumentRoot "/Users/<user-name>/Sites/<site-name>"
    	ServerName <server-name>
    </VirtualHost>

## Start Apache

Start (or `restart`) Apache to activate new config

    sudo apachectl start

# PHP

Create a `php.ini` file

    sudo cp /private/etc/php.ini.default /private/etc/php.ini

(For additional error reporting when developing, download the related distribution from [php.net/releases](http://php.net/releases/) and use `php.ini-development` contents for `php.ini` config)

Add your timezone to date.timezone to stop PHP date warning (eg. `America/Los_Angeles`)

    date.timezone = "<timezone>"

Configure MySQL socket setting, find and set the following

    pdo_mysql.default_socket = /tmp/mysql.sock
    mysqli.default_socket = /tmp/mysql.sock

# Hosts File

Open the etc hosts file

    /private/etc/hosts

Add entries for each virtual host

    127.0.0.1 <domain-name>

# MySQL

Install MySQL with Homebrew (Latest: `msyql` or Version: `msyql@5.7`)

    brew install mysql@5.7

And MySQL bin folder to path (reload shell to activate)

    export PATH=/usr/local/opt/mysql@5.7/bin:$PATH

Start MySQL server

    mysql.server start

Secure MySQL installation

    mysql_secure_installation

Step through MySQL secure installation procedure

- Set a root password
- Remove anonymous user
- Disallow root login remotely
- Remove test databases
- Reload privileges

# General Information

## Useful Files and Directories

Default user sites location

    ~/Sites

Base Apache files location

    /Library/WebServer

Default Apache page (contains default index page)

    /Library/WebServer/Documents

Location of MySQL database files

    /usr/local/var/mysql
