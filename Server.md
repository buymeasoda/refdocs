# Server

## Login

Log in to server and use root password (accept new fingerprint)

    ssh root@<server-ip>
    ssh root@12.34.567.890

Use `-i` flag to allow selection of an ssh private key if you have multiple

## Upgrade Server

Update server packages and upgrade system

    sudo apt-get update
    sudo apt-get upgrade

## Set Hostname

Set machine hostname

    hostnamectl set-hostname <host-name>

Alternatively set hostname manually

    echo "<host-name>" > /etc/hostname
    hostname -F /etc/hostname

Check hostname

    hostname

## Set Hosts

Add server IP entry and hostname for FQDN (fully qualified domain name) to `/etc/hosts`

    <server-ip> <fqdn> <host-name>
    12.34.567.890 host.domain.ext yourhostname

## Configure FQDN DNS

Set the following DNS records to point to the server IP via DNS admin for the fully qualified domain name

- Point "A" record to server IPv4 address
- Point "AAAA" record to server IPv6 address (if IPv6 enabled)

## Set Timezone

Set the timezone

    dpkg-reconfigure tzdata

Check the server time

    date

# User and SSH Setup

## Create Limited User

Create new limited user account and set a password (skip account details with enter)

    adduser <user-name>

Add user to sudo group

    adduser <user-name> sudo

Exit and log in as new user

    exit
    ssh <user-name>@<server-ip>

## Set up SSH key

Create an RSA SSH key pair if you do not have one (on local machine)

    ssh-keygen -b 4096

Make an .ssh directory on the server if one doesn't exist

    mkdir -p ~/.ssh && sudo chmod -R 700 ~/.ssh/

Copy public key from local machine `authorized_keys` file

    scp ~/.ssh/id_rsa.pub <user-name>@<server-ip>:~/.ssh/authorized_keys

Set permissions on `authorized_keys` file on the server

    chmod 600 .ssh/authorized_keys

## Configure SSH Daemon

Edit the sshd config file

    sudo nano /etc/ssh/sshd_config

Modify (or add) the following sshd_config settings

    AllowUsers <user-name>
    Port <Random port between 1025 and 65536>
    PermitRootLogin no
    PasswordAuthentication no
    AddressFamily inet

Use `AddressFamily inet` to limit to IPv4 or `AddressFamily inet6` for IPv6

Reload ssh daemon config

    sudo systemctl restart sshd

## Configure Firewall

Set initial default configuration

    sudo ufw default allow outgoing
    sudo ufw default deny incoming

Configure http/s and ssh (use custom ssh port or ssh/tcp for default port 22)

    sudo ufw allow http/tcp
    sudo ufw allow https/tcp
    sudo ufw allow <custom-ssh-port>/tcp

Set firewall logging on (logs output to `/etc/logs/`)

    sudo ufw logging on

Check status of firewall rules (add verbose for details about logging)

    sudo ufw status
    sudo ufw status verbose

View UFW log files

    sudo less /var/log/ufw.log

## Remove Unused Services

View list of network running services (note package name)

    sudo netstat -tulpn

Remove unused service package if not required

    sudo apt-get purge <package-name>

# Webserver

## Apache

Install Apache web server

    sudo apt-get install apache2

Configure Apache base settings

    sudo nano /etc/apache2/conf-available/security.conf

Set the following configuration settings in `security.conf`

    ServerTokens Prod
    ServerSignature Off

Disable auto file listings and HTML based directory navigation

    sudo a2dismod autoindex

Disable the default test page (and replace the default html file at `/var/www/html` with a blank `index.html`)

    sudo a2dissite 000-default.conf

Disable MPM Event and set MPM to Prefork for PHP (`mod_php`)

    sudo a2dismod mpm_event
    sudo a2enmod mpm_prefork

Start and stop the apache server

    sudo systemctl start apache2
    sudo systemctl stop apache2
    sudo systemctl restart apache2

Reload apache configuration and show status

    sudo systemctl reload apache2
    systemctl status apache2

## MySQL Server

Install MySQL Server (add a root user password when prompted)

    sudo apt-get install mysql-server

Run MySQL secure installation and follow prompts

    mysql_secure_installation

Create a `utf8.cnf` file to configure MySQL for UTF8

    sudo nano /etc/msyql/conf.d/utf8.cnf

Add the following rules to `utf8.cnf`

    [client]
    default-character-set=utf8
    [mysqld]
    character-set-server=utf8

Restart MySQL Server

    sudo systemctl restart mysql

Log in to MySQL Server

    mysql -u root -p

Check character set settings are correct

    mysql> show variables like 'char%';

Alternatively check from settings output

    mysql> \s

MySQL commands

    sudo systemctl stop mysql
    sudo systemctl start mysql
    sudo systemctl restart mysql

## PHP

Install base PHP and additional PHP features

    sudo apt-get install php7.0 libapache2-mod-php7.0 php7.0-mysql php7.0-curl php7.0-gd php7.0-cli php7.0-xml

Create php log directory

    sudo mkdir /var/log/php
    sudo chown www-data /var/log/php

Configure `php.ini` for logging

    sudo nano /etc/php/7.0/apache2/php.ini

Add or update the error log file rule location

    error_log = /var/log/php/error.log

Restart/reload Apache for changes to apply

    sudo systemctl restart apache2
    sudo systemctl reload apache2

## Mail

Install Postfix to allow PHP to send email

    sudo apt-get install libsasl2-modules postfix

Set up using the following values

    Mail type configuration: Internet Site
    Host Name: <mail-hostname>

Postfix settings file (confirm host name is set correctly)

    /etc/postfix/main.cf

Configure mail to send/receive only from the local host (main.cf)

    inet_interfaces = loopback-only

Restart postfix after making configuration changes

    sudo systemctl restart postfix

Postfix commands (status | start | stop | reload | restart)

    sudo systemctl <command> postfix

Send a test email using sendmail via command line (finish command with .)

    sendmail recipient@elsewhere.com
    From: you@example.com
    Subject: Test mail
    This is a test email
    .

Send a test email one line command (add `-v` to generate debug information `/var/mail/<user>`)

    echo "Subject: Test email" | sendmail you@example.com

## Git

Install and configure git

    sudo apt-get install git

# Web site setup

## Manage sites with git

Create bare repo on server

    git init --bare <path>/<repo>

Add remote bare repo as an origin for local repo and push

    git remote add origin ssh://<server>/<path>/<repo>
    git push origin master

Clone repo to www directory on server

    sudo git clone <path>/<repo> /var/www/<site>

## Set folder and file permissions

Allow Apache write permission for folders used by upload scripts (eg. CMS uploads)

    sudo chmod 775 <folder>
    sudo chgrp www-data <folder>

## Configure and enable sites

Web server site directories

    /var/www/<site>

Create and edit virtual host configuration file

    sudo nano /etc/apache2/sites-available/<site>.conf

Enable/Disable site configuration

    sudo a2ensite <site>.conf
    sudo a2dissite <site>.conf

Reload Apache to apply changes

    sudo systemctl reload apache2

## Add Subdomains

- Using DNS Manager add a new A/AAAA record for the domain
- Add a virtual hosts entry for your subdomain in the Apache site conf
- Reload Apache configuration (DNS propagation for new entries will depend on TTL)

# Database Setup

## Import/Export Database

Export database data from existing DB

    mysqldump -u root -p <database> > <file.sql>

Import database data into new DB

    mysqladmin -u root -p create <database>
    mysql -u root -p <database> < <file.sql>

## Configure Database

Log in to MySQL Server

    mysql -u root -p

List the databases

    show databases;

Create general user

    CREATE USER <user>@localhost IDENTIFIED BY '<password>';
    FLUSH PRIVILEGES;

Grant general privileges

    GRANT SELECT, INSERT, UPDATE, DELETE ON <database>.* TO <user>@localhost;
    FLUSH PRIVILEGES;

Get list of users

    SELECT User FROM mysql.user;

Show permission for user

    SHOW GRANTS FOR <user>@localhost;

General database commands

    use <database>;
    show tables;
    select * from <table>;

# Crontab Setup

List (`-l`), edit (`-e`) and remove (`-r`) crontab entries

    crontab -l
    crontab -e
    crontab -r

Edit crontab for a different user

    sudo -u <user> crontab -e

# Server Reboot Management

Display which services are currently running, and which are listed to start on boot

    sudo service --status-all

# Domain management and DNS configuration

## Set name servers

Set domain name server entries for host via domain registrar admin

## Add email SPF rules

Add A record for SPF rule to allow scripts to send email from server via google

Google sending only

    v=spf1 include:_spf.google.com ~all

Google and domain allowed to send

    v=spf1 a include:_spf.google.com ~all

## Configure Reverse DNS

Set reverse DNS via host DNS manager to use server configured fully qualified domain name (FQDN)

# Additional debugging and logs

## Admin Mail

Local user mail messages

    cat /var/mail/<user>

Empty system mail file for user using `>`

    > /var/mail/<user>

## DNS Status

Check DNS status and update time remaining ("Answer" section shows time remaining in seconds)

    dig <domain>

Check DNS status for a specific domain name server

    dig @<dns-server> <domain>

## Logs

View PHP and Apache error log output

    tail -f /var/log/php/error.log
    sudo tail -f /var/log/apache2/error.log

Browse other log files

    cd /var/log/

Empty log files using `>`

    > /var/log/<log-file>

## Apache

View server status web summary

    curl localhost/server-status

Test mod default gzip (fetch with and without gzip header to compare) on a uncompressed js or css file

    wget --header="Accept-Encoding: gzip" http://<domain>/<file>
