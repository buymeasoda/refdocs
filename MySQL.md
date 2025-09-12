# MySQL

Reference for working with [MySQL](http://www.mysql.com/).

For database, table and column names that are reserved words or irregular names, surround the names with backticks `` ` ``. For string values, wrap the values with single `'` or double `"` quotes.

If you are operating on a local MySQL database, `<host>` in the examples below will be `localhost`.

## Install MySQL Server

Linux

    sudo apt-get install mysql-server

macOS

    brew install mysql

Secure MySQL installation

    mysql_secure_installation

macOS post install instructions via homebrew

    unset TMPDIR
    mysql_install_db
    mysql.server start
    mysql_secure_installation

## MySQL Information

Show installed MySQL version

    mysql -V

## Control MySQL Server

Linux

    service mysql start | stop | restart | status

macOS

    mysql.server start | stop | restart | status
    mysql.server reload | force-reload

Run MySQL as a background service (Homebrew / macOS)

    brew services start mysql@<version>

macOS homebrew executable location

    /usr/local/Cellar/mysql/<version>/support-files

## Log In/Out

Log into MySQL as `root`

    mysql -u root -p

Log into MySQL as `<user>`

    mysql -u <user> -p

Exit MySQL

    mysql> exit

## Database Files

Linux

    /var/lib/mysql

macOS

    /usr/local/var/mysql

Report total size of MySQL databases

    sudo du -skh <mysql-directory>

## Manage Users

Create a user

    CREATE USER '<user>'@'<host>' IDENTIFIED BY '<password>';
    FLUSH PRIVILEGES;

Delete a user

    DROP USER '<user>'@'<host>';

Change a user's password (as root)

    SET PASSWORD FOR '<user>'@'<host>' = PASSWORD('<password>');

Show list of users

    SELECT User FROM mysql.user;

## Manage Privileges

Assign database privileges

Privileges:

- SELECT - Read only
- INSERT - Insert rows/data
- UPDATE - Change inserted rows/data
- DELETE - Delete drop rows of data
- CREATE - Create new tables
- ALTER - Change table/column names
- DROP - Drop columns/tables

Grant all privileges

    GRANT ALL PRIVILEGES ON <database>.* TO '<user>'@'<host>';
    FLUSH PRIVILEGES;

Grant general privileges

    GRANT SELECT, INSERT, UPDATE, DELETE ON <database>.* TO '<user>'@'<host>';
    FLUSH PRIVILEGES;

Grant table privileges

    GRANT CREATE, DROP, ALTER ON <database>.* TO '<user>'@'<host>';

Revoke all privileges

    REVOKE ALL ON <database>.* FROM '<user>'@'<host>';

Revoke specific privileges

    REVOKE DELETE, INSERT ON <database>.* FROM '<user>'@'<host>';

Show privileges

    SHOW GRANTS FOR '<user>'@'<host>';

## Navigate Databases and Tables

Show list of available databases

    SHOW DATABASES;

Select database to use for subsequent SQL commands

    USE <database>;

Show tables for selected database

    SHOW TABLES;

Show the column names and column types for a table

    DESCRIBE <table>;

Show all rows that exist in a column

    SELECT * FROM <column>;

## Create and Delete databases

Create a new database

    CREATE DATABASE <database>;

Delete an existing database

    DROP DATABASE <database>;

## Create, Delete and Alter Tables

Create a table and columns

    CREATE TABLE <table> (<column> <type> <settings>);

Create a table and columns (example)

    CREATE TABLE <table> (id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, <column> VARCHAR(45));

Rename table

    RENAME TABLE <table> to <new table>;

Delete table

    DROP TABLE <table>;

Add table column

    ALTER TABLE <table> ADD <column> <type> <settings>;

Add table column in location (example)

    ALTER TABLE <table> ADD <new column> VARCHAR(45) NULL AFTER `<column>`;

Insert record

    INSERT INTO <table> (<column>, <other column>) VALUES ('<value>', '<other value>');

## Select, Update and Delete Rows

Select records

    SELECT * FROM <table>;

Update record

    UPDATE <table> SET <column> = '<value>';

Update record with condition

    UPDATE <table> SET <column> = '<value>' WHERE <table>.<other column> = <condition>;

Delete all rows

    DELETE FROM <table>;

Delete specific record

    DELETE FROM <table> WHERE <table>.<column> = '<value>';

## Using Wildcards

Wildcards via `%` can be used for grants on database names (literal underscores must be escaped `\_`)

Grant select for databases that match `foo_*` (eg. `foo_bar`, `foo_qux`)

    GRANT SELECT ON `foo\_%`.* TO '<user>'@'<host>';

Revoke all for `foo_*`

    REVOKE ALL ON `foo\_%`.* TO '<user>'@'<host>';

Note: Grants and revokes made in this manner must match the same wildcard value (eg. `foo\_%`)

## MySQL Database Import / Export

Export database

    mysqldump -u root -p <database> > <file.sql>

Import database

    mysqladmin -u root -p create <database>
    mysql -u root -p <database> < <file.sql>

Executing .sql files

    mysql> source <file.sql>

Alternative way to execute .sql files

    mysql> \. <file.sql>

Output MySQL settings

    mysql> \s

## Rename Database

    mysqldump -u root -p -v <database> > <file.sql>
    mysqladmin -u root -p create <new database>
    mysql -u root -p <new database> < <file.sql>

## Check Database Configuration

Show current character set configuration

    SHOW VARIABLES LIKE 'char%';

Show database variables

    mysqladmin -u <user> -p variables
