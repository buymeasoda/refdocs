
# MySQL

Reference for working with [MySQL](http://www.mysql.com/).
    
For database, table and column names that are reserved words or irregular names, surround the names with backticks `` ` ``. For string values, wrap the values with single `'` or double `"` quotes.

If you are operating on a local MySQL database, `<host>` in the examples below will be `localhost`.


## Install MySQL Server

    sudo apt-get install mysql-server
    mysql_secure_installation


## Control MySQL Server

Start, stop and restart MySQL Server

    sudo service mysql start
    sudo service mysql stop
    sudo service mysql restart


## Logging in and out

Log into MySQL as `root`

    $ mysql -u root -p

Log into MySQL as `<user>`
    
    $ mysql -u <user> -p
    
Exit MySQL

    mysql> exit


## Database files

Location of MySQL databases

    /var/lib/mysql

Report total size of MySQL databases

    sudo du -skh /var/lib/mysql


## Managing Users

Create a user
    
    mysql> CREATE USER '<user>'@'<host>' IDENTIFIED BY '<password>';
    mysql> FLUSH PRIVILEGES;

Delete a user

    mysql> DROP USER '<user>'@'<host>';

Change a user's password (as root)

    mysql> SET PASSWORD FOR '<user>'@'<host>' = PASSWORD('<password>');
    
Show list of users

    mysql> SELECT User FROM mysql.user;


## Managing user privileges

Assign database privileges

Privileges:

* SELECT - Read only
* INSERT - Insert rows/data
* UPDATE - Change inserted rows/data
* DELETE - Delete drop rows of data
* CREATE - Create new tables
* ALTER - Change table/column names
* DROP - Drop columns/tables

Grant all privileges

    mysql> GRANT ALL PRIVILEGES ON <database>.* TO '<user>'@'<host>';
    mysql> FLUSH PRIVILEGES;

Grant general privileges

    mysql> GRANT SELECT, INSERT, UPDATE, DELETE ON <database>.* TO '<user>'@'<host>';
    mysql> FLUSH PRIVILEGES;

Grant table privileges
    
    mysql> GRANT CREATE, DROP, ALTER ON <database>.* TO '<user>'@'<host>';

Revoke all privileges

    mysql> REVOKE ALL ON <database>.* FROM '<user>'@'<host>';
    
Revoke specific privileges

    mysql> REVOKE DELETE, INSERT ON <database>.* FROM '<user>'@'<host>';

Show privileges

    mysql> SHOW GRANTS FOR '<user>'@'<host>';


## Navigating Databases and Tables

Show list of available databases

	mysql> SHOW DATABASES;
		
Select database to use for subsequent SQL commands

	mysql> USE <database>;
		
Show tables for selected database

	mysql> SHOW TABLES;
		
Show the column names and column types for a table

	mysql> DESCRIBE <table>;
		
Show all rows that exist in a column

	mysql> SELECT * FROM <column>;


## Create and delete databases

Create a new database

    mysql> CREATE DATABASE <database>;
	
Delete an existing database

    mysql> DROP DATABASE <database>;


## Create, delete and alter tables

Create a table and columns

    mysql> CREATE TABLE <table> (<column> <type> <settings>);
	
Create a table and columns (example)

    mysql> CREATE TABLE <table> (id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, <column> VARCHAR(45));

Create a new table or a backup table from an existing one

    mysql> CREATE TABLE <new_table> AS SELECT * FROM <existing_table>;
	
Rename table

    mysql> RENAME TABLE <table> to <new table>;

Delete table

    mysql> DROP TABLE <table>;

Add table column
    
    mysql> ALTER TABLE <table> ADD <column> <type> <settings>;
    
Add table column in location (example)

    mysql> ALTER TABLE <table> ADD <new column> VARCHAR(45) NULL AFTER `<column>`;

Insert record

    mysql> INSERT INTO <table> (<column>, <other column>) VALUES ('<value>', '<other value>');


## Constraints
Add a composite primary key in an existing table with a single primary key already defined

    mysql> ALTER TABLE <table> DROP PRIMARY KEY, ADD CONSTRAINT <pk_name> PRIMARY KEY (<column>, <column>);

Add a foreign key constraint at table creation 
**note:** *Parent table must already exist*

    mysql> CREATE TABLE <table> ( 
                id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, 
                <column> VARCHAR(45),
                <column> CHAR(13),
                parent_id INT NOT NULL,
                CONSTRAINT <fk_name> FOREIGN KEY(parent_id) REFERENCES <parent_table>(id) ON DELETE CASCADE|RESTRICT;
           );

Add a foreign key constraint to an existing table 
**note:** *Rows must already have a valid value that maps to the parent table's row for the colum which we'are making a foreign key*

    mysql> ALTER TABLE <table> 
           ADD CONSTRAINT <fk_name> FOREIGN KEY(parent_id) REFERENCES <parent_table>(id) ON DELETE CASCADE|RESTRICT;

Remove a foreign key constraint

    mysql> ALTER TABLE <table> DROP FOREIGN KEY <fk_name>;


## Select, update and delete rows

Select records

    mysql> SELECT * FROM <table>;

Update record

    mysql> UPDATE <table> SET <column> = '<value>';

Update record with condition

    mysql> UPDATE <table> SET <column> = '<value>' WHERE <table>.<other column> = <condition>;

Delete all rows

    mysql> DELETE FROM <table>;

Delete specific record

    mysql> DELETE FROM <table> WHERE <table>.<column> = '<value>';


## MySQL Database Import / Export

Export database

    $ mysqldump -u root -p <database> > <file.sql>

Import database

    $ mysqladmin -u root -p create <database>
    $ mysql -u root -p <database> < <file.sql>

Executing .sql files

    mysql> source <file.sql>
    
Alternative way to execute .sql files

    mysql> \. <file.sql>

Output MySQL settings

    mysql> \s


## Rename MySQL Database

    $ mysqldump -u root -p -v <database> > <file.sql>
    $ mysqladmin -u root -p create <new database>
    $ mysql -u root -p <new database> < <file.sql>


## Setting up server for utf8

Show current character set configuration

    mysql> show variables like 'char%';

Configuring MySQL utf8

In my.cnf:

    [mysqld]
    character-set-server=utf8

    [client]
    default-character-set=utf8

For html document creation / saving: Set file encoding type to utf8