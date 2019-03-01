# Apache

## Control Server

Start and stop Apache server

    sudo apachectl start
    sudo apachectl stop

Restart Apache server and apply new configuration

    sudo apachectl restart

Check apache server process is running

    ps -aef | grep httpd

## Check Configuration

Run syntax check for config files

    apachectl -t
    apachectl configtest

## Show Configuration

Show Apache version and compile settings module details

    apachectl -v
    apachectl -V

List available configuration directives

    apachectl -L

List compiled (`-l`) and loaded modules (`-M` same as `-t -D DUMP_MODULES`)

    apachectl -l
    apachectl -M

Show parsed vhosts config and run settings (same as `-t -D DUMP_VHOSTS -D DUMP_RUN_CFG`)

    apachectl -S

Output summary debug information for Apache (modules, vhosts, config)

    apachectl -t -D DUMP_MODULES
    apachectl -t -D DUMP_VHOSTS
    apachectl -t -D DUMP_RUN_CFG
