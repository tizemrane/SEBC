## Verify user privileges
```
[tizemrane@n1 ~]$ klist
Ticket cache: FILE:/tmp/krb5cc_2001
Default principal: tizemrane@SEBC.COM

Valid starting     Expires            Service principal
10/17/18 22:38:38  10/18/18 22:38:38  krbtgt/SEBC.COM@SEBC.COM
        renew until 10/17/18 22:38:38
[tizemrane@n1 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://n2.sebcdomain:10000/default;principal=hive/n2.sebcdomain@SEBC.COM
Connecting to jdbc:hive2://n2.sebcdomain:10000/default;principal=hive/n2.sebcdomain@SEBC.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://n2.sebcdomain:10000/default> show tables
. . . . . . . . . . . . . . . . . . . . . .> ;
INFO  : Compiling command(queryId=hive_20181017224040_bd303096-6282-43d6-89cd-9530e64979d9): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017224040_bd303096-6282-43d6-89cd-9530e64979d9); Time taken: 4.409 seconds
INFO  : Executing command(queryId=hive_20181017224040_bd303096-6282-43d6-89cd-9530e64979d9): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017224040_bd303096-6282-43d6-89cd-9530e64979d9); Time taken: 3.418 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (10.443 seconds)
```

## Create a Sentry role with full authorization

```
0: jdbc:hive2://n2.sebcdomain:10000/default> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181017224444_951d6387-d760-4905-be01-c2e8c8c1be5e): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017224444_951d6387-d760-4905-be01-c2e8c8c1be5e); Time taken: 0.581 seconds
INFO  : Executing command(queryId=hive_20181017224444_951d6387-d760-4905-be01-c2e8c8c1be5e): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017224444_951d6387-d760-4905-be01-c2e8c8c1be5e); Time taken: 0.308 seconds
INFO  : OK
No rows affected (0.978 seconds)
0: jdbc:hive2://n2.sebcdomain:10000/default> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20181017225151_cadfbe11-66f9-4754-acd0-beb454d29181): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017225151_cadfbe11-66f9-4754-acd0-beb454d29181); Time taken: 0.659 seconds
INFO  : Executing command(queryId=hive_20181017225151_cadfbe11-66f9-4754-acd0-beb454d29181): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017225151_cadfbe11-66f9-4754-acd0-beb454d29181); Time taken: 0.283 seconds
INFO  : OK
No rows affected (1.034 seconds)
0: jdbc:hive2://n2.sebcdomain:10000/default> GRANT ROLE sentry_admin TO GROUP tizemrane;
INFO  : Compiling command(queryId=hive_20181017225151_fd179375-99fc-43df-8d55-879411dd8530): GRANT ROLE sentry_admin TO GROUP tizemrane
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20181017225151_fd179375-99fc-43df-8d55-879411dd8530); Time taken: 0.448 seconds
INFO  : Executing command(queryId=hive_20181017225151_fd179375-99fc-43df-8d55-879411dd8530): GRANT ROLE sentry_admin TO GROUP tizemrane
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017225151_fd179375-99fc-43df-8d55-879411dd8530); Time taken: 0.163 seconds
INFO  : OK
No rows affected (0.699 seconds)
0: jdbc:hive2://n2.sebcdomain:10000/default> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20181017225151_5f7f7939-5311-4323-bdd2-b6640dc8832b): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017225151_5f7f7939-5311-4323-bdd2-b6640dc8832b); Time taken: 0.472 seconds
INFO  : Executing command(queryId=hive_20181017225151_5f7f7939-5311-4323-bdd2-b6640dc8832b): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017225151_5f7f7939-5311-4323-bdd2-b6640dc8832b); Time taken: 0.729 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (1.795 seconds)

```

## kinit as george

```
[tizemrane@n1 ~]$ kinit george
Password for george@SEBC.COM:
[tizemrane@n1 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://n2.sebcdomain:10000/default;principal=hive/n2.sebcdomain@SEBC.COM
scan complete in 4ms
Connecting to jdbc:hive2://n2.sebcdomain:10000/default;principal=hive/n2.sebcdomain@SEBC.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://n2.sebcdomain:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20181017230606_8b77df3c-f197-4977-b860-e49d3c5af7a9): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017230606_8b77df3c-f197-4977-b860-e49d3c5af7a9); Time taken: 0.472 seconds
INFO  : Executing command(queryId=hive_20181017230606_8b77df3c-f197-4977-b860-e49d3c5af7a9): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017230606_8b77df3c-f197-4977-b860-e49d3c5af7a9); Time taken: 1.233 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (1.996 seconds)
```

## kinit as ferdinand

```
[tizemrane@n1 ~]$ kinit ferdinand
Password for ferdinand@SEBC.COM:
[tizemrane@n1 ~]$ beeline
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Beeline version 1.1.0-cdh5.13.3 by Apache Hive
beeline> !connect jdbc:hive2://n2.sebcdomain:10000/default;principal=hive/n2.sebcdomain@SEBC.COM
scan complete in 4ms
Connecting to jdbc:hive2://n2.sebcdomain:10000/default;principal=hive/n2.sebcdomain@SEBC.COM
Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://n2.sebcdomain:10000/default> show tables;
INFO  : Compiling command(queryId=hive_20181017230707_2631338d-af0d-4489-9a0a-3c24319e3079): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20181017230707_2631338d-af0d-4489-9a0a-3c24319e3079); Time taken: 0.539 seconds
INFO  : Executing command(queryId=hive_20181017230707_2631338d-af0d-4489-9a0a-3c24319e3079): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20181017230707_2631338d-af0d-4489-9a0a-3c24319e3079); Time taken: 0.871 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (1.651 seconds)

```