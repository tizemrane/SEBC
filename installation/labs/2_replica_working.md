## <center> MySQL/MariaDB Installation Lab
## <center> <a name="mysql_replication_lab"/>Configure MySQL with a replica server

Choose one of these plans to follow:

* You can use the steps [documented here for
MariaDB](http://www.cloudera.com/documentation/enterprise/latest/topics/install_cm_mariadb.html)
or [here for MySQL](http://www.cloudera.com/documentation/enterprise/latest/topics/cm_ig_mysql.html).<br>
* The steps below are MySQL-specific.
  *  If you are using RHEL/CentOS 7.x, **use MariaDB**.

---
<div style="page-break-after: always;"></div>

## <center> MySQL installation - Plan Two Detail

1. Download and implement the [official MySQL repo](http://dev.mysql.com/downloads/repo/yum/)
    * Enable the repo to install MySQL 5.5
    * Install the <code>mysql</code> package on all nodes
    * Install <code>mysql-server</code> on the server and replica nodes
    * Download and copy [the JDBC connector](https://dev.mysql.com/doc/connector-j/5.1/en/connector-j-binary-installation.html) to all nodes.
```
## Installing wget and Downloading mysql-repo-package in all nodes
> sudo yum install wget
> wget https://dev.mysql.com/get/mysql80-community-release-el6-1.noarch.rpm

## Installing the package

> sudo rpm -ivh mysql80-community-release-el6-1.noarch.rpm
warning: mysql80-community-release-el6-1.noarch.rpm: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Preparing...                ########################################### [100%]
   1:mysql80-community-relea########################################### [100%]

## Installing yum-utils ==> In Centos 6 the yum-config-manager is not installed
> sudo yum install yum-utils

## Enabling the 5.5 package

> sudo yum-config-manager --disable mysql80-community
> sudo yum-config-manager --enable mysql55-community

> sudo yum repolist enabled | grep mysql
mysql-connectors-community           MySQL Connectors Community              59
mysql-tools-community                MySQL Tools Community                   65
mysql55-community                    MySQL 5.5 Community Server             468

## Installing mysql client package in all nodes
> sudo yum install mysql -y

## Installing mysql-community-server in n1 and n2 nodes
> sudo yum install mysql-community-server

## Installing and configuring the jdbc connector in all nodes
> wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.46.tar.gz

> tar zxvf mysql-connector-java-5.1.46.tar.gz

> sudo mkdir -p /usr/share/java/
> cd mysql-connector-java-5.1.46
> sudo cp mysql-connector-java-5.1.46-bin.jar /usr/share/java/mysql-connector-java.jar

```
2. You should not need to build a <code>/etc/my.cnf</code> file to start your MySQL server
    * You will have to modify it to support replication. Check MySQL documentation.<p>
```
## adding configurations for replication 

## in node n1
log_bin=/var/lib/mysql/mysql_binary_log
log-bin=mysql-bin
server_id=1

## in node n2
server_id=2
```
3. Start the <code>mysqld</code> service.
```
> sudo service mysqld start
```
4. Use <code>/usr/bin/mysql_secure_installation</code> to:<br>
    a. Set password protection for the server<br>
    b. Revoke permissions for anonymous users<br>
    c. Permit remote privileged login<br>
    d. Remove test databases<br>
    e. Refresh privileges in memory<br>
    f. Refreshes the <code>mysqld</code> service<p>
```
[tarek@n1 ~]$ sudo mysql_secure_installation




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] Y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!

```
5. On the master MySQL node, grant replication privileges for your replica node:<br>
    a. Log in with <code>mysql -u ... -p</code> <br>
    b. Note the FQDN of your replica host.<br>
    c. <code>mysql> **GRANT REPLICATION SLAVE ON \*.\* TO '*user*'@'*FQDN*' IDENTIFIED BY '*password*';**</code><br>
    d. <code>mysql> **SET GLOBAL binlog_format = 'ROW';** </code><br>
    e. <code>mysql> **FLUSH TABLES WITH READ LOCK;</code>**<p>

```
mysql> GRANT REPLICATION SLAVE ON *.* TO slave@172.31.19.154 IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)

mysql> SET GLOBAL binlog_format = 'ROW';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH TABLES WITH READ LOCK;
Query OK, 0 rows affected (0.00 sec)
```

6. In a second terminal session, log into the MySQL master and show its  status:<br>
    a. <code>mysql> **SHOW MASTER STATUS;**</code><br>
    b. Make note of the file name and byte offset. The replica needs this info to sync to the master.<br>
    c. Logout of the second session; remove the lock on the first with <code>mysql> **UNLOCK TABLES;**</code><p>

```
mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000003 |     1213 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)

```
7. Login to the replica server and configure a connection to the master:<br>
    <code>mysql> **CHANGE MASTER TO**<br> **MASTER_HOST='*master host*',**<br> **MASTER_USER='*replica user*',**<br> **MASTER_PASSWORD='*replica password*',**<br> **MASTER_LOG_FILE='*master file name*',**<br> **MASTER_LOG_POS=*master file offset*;**</code><p>

```
mysql> CHANGE MASTER TO MASTER_HOST='172.31.24.141', MASTER_USER='slave', MASTER_PASSWORD='password', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=1213;
Query OK, 0 rows affected (0.02 sec)

mysql> START SLAVE;
Query OK, 0 rows affected (0.00 sec)
```

8. Initiate slave operations on the replica<br>
    a. <code>mysql> **START SLAVE;**</code><br>
    b. <code>mysql> **SHOW SLAVE STATUS \G**</code><br>
    c. If successful, the <code>Slave_IO_State</code> field will read <code>Waiting for master to send event</code><br>
    d. Once successful, capture this output and store it in <code>labs/2_replica_working.md</code><br>
    e. Review your log (<code>/var/log/mysqld.log</code>) for errors. If stuck, consult with a colleague or instructor.<p>

```
mysql> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: 172.31.24.141
                  Master_User: slave
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000003
          Read_Master_Log_Pos: 1213
               Relay_Log_File: mysqld-relay-bin.000002
                Relay_Log_Pos: 253
        Relay_Master_Log_File: mysql-bin.000003
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB:
          Replicate_Ignore_DB:
           Replicate_Do_Table:
       Replicate_Ignore_Table:
      Replicate_Wild_Do_Table:
  Replicate_Wild_Ignore_Table:
                   Last_Errno: 0
                   Last_Error:
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 1213
              Relay_Log_Space: 410
              Until_Condition: None
               Until_Log_File:
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File:
           Master_SSL_CA_Path:
              Master_SSL_Cert:
            Master_SSL_Cipher:
               Master_SSL_Key:
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error:
               Last_SQL_Errno: 0
               Last_SQL_Error:
  Replicate_Ignore_Server_Ids:
             Master_Server_Id: 1
1 row in set (0.00 sec)

```

---
<div style="page-break-after: always;"></div>