Due to incompatiable version of OS , I have lost a lot of time in setting up the service.

yum install mysql-community-server

mysql -u -p
set password for 'root'@'localhost' = password ('auth_string');

yum install mysql-connector-java

yum repolist enabled | grep mysql
root@\Barlearn1$ yum repolist enabled | grep mysql
mysql-connectors-community MySQL Connectors Community 24
mysql-tools-community MySQL Tools Community 42
mysql55-community MySQL 5.5 Community Server 316

add to file my.cnf on Server1 path /etc with the below settings:
[mysqld]
log-bin=mysql-bin
server-id	= 1
auto_increment_increment = 10
auto_increment_offset = 1

Change mode/permission for my.cnf to rw_r__r_ else mysql will igonore it.
sudo chmod 644 my.cnf

Stop and start mysql.

create user replicant@'%' identified by 'password';
GRANT SELECT, PROCESS, FILE, SUPER, REPLICATION CLIENT, REPLICATION SLAVE, RELOAD ON . TO replicant@'%';
flush Privileges;

On the master MySQL node, grant replication privileges for your replica node:
a. Log in with mysql -u ... -p
b. Note the FQDN of your replica host.
c. mysql> GRANT REPLICATION SLAVE ON . TO 'user'@'FQDN' IDENTIFIED BY 'password';
d. mysql> SET GLOBAL binlog_format = 'ROW';
e. mysql> FLUSH TABLES WITH READ LOCK;

In a second terminal session, log into the MySQL master and show its status:
a. mysql> SHOW MASTER STATUS;
b. Make note of the file name and byte offset. The replica needs this info to sync to the master.
c. Logout of the second session; remove the lock on the first with mysql> UNLOCK TABLES;

Incomplete - Discussed with James as too many issues to troubleshoot. So continued with Single / Standalone set up.
