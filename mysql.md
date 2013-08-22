# How-Tos

## Create Database and User
DBUSER=foo; DBUSERPW=123; DBNAME=foo;  mysql -e "create database if not exists $DBNAME; grant all privileges on $DBNAME.* to '$DBUSER'@'127.0.0.1' identified by '$DBUSERPW';grant all privileges on $DBNAME.* to '$DBUSER'@'localhost' identified by '$DBUSERPW';FLUSH PRIVILEGES;"


## Drop Huge Tables

    CREATE TABLE new_sys_log LIKE sys_log;
    RENAME TABLE sys_log TO old_sys_log, new_sys_log TO sys_log;
    DROP TABLE old_sys_log;

## Becoming MySQL-root on Debian-based Systems
Needs to be run with root priviledges.

	mysql --defaults-extra-file=/etc/mysql/debian.cnf

<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
