# How-Tos

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
