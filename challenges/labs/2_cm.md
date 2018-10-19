### ls /etc/yum.repos.d

```
[tarek@t2 ~]$ ls /etc/yum.repos.d
CentOS-Base.repo       CentOS-Media.repo  cloudera-manager.repo  epel-testing.repo     mysql-community-source.repo
CentOS-Debuginfo.repo  CentOS-Vault.repo  epel.repo              mysql-community.repo
```

### Configure Cloudera Manager

```
[tarek@t2 ~]$ sudo /usr/share/cmf/schema/scm_prepare_database.sh  mysql scm scmuser password -h 172.31.22.226  -P 3306
JAVA_HOME=/usr/java/jdk1.8.0_162
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.8.0_162/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
log4j:ERROR Could not find value for key log4j.appender.A
log4j:ERROR Could not instantiate appender named "A".
[2018-10-19 08:06:25,215] INFO     0[main] - com.cloudera.enterprise.dbutil.DbCommandExecutor.testDbConnection(DbCommandExecutor.java) - Successfully connected to database.
All done, your SCM database is configured correctly!

```