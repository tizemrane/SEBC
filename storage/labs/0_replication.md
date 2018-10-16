## <center> HDFS Lab: Replicate to another cluster

Node: Data replication in the cloud depends on peers that can see each
other's nodes.

* Choose a partner in class
* Name a source directory after your GitHub handle
* Name a target directory after your partner's GitHub handle
```
[tarek@n2 ~]$ hdfs dfs -mkdir Isalah89
[tarek@n2 ~]$ hdfs dfs -mkdir tizemrane
```
* Use `teragen` to create a 500 MB file
```
[tarek@n2 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen 5000000 /user/tarek/tizemrane/teragen-output

[tarek@n2 ~]$ hdfs dfs -ls -h /user/tarek/tizemrane/*
Found 3 items
-rw-r--r--   3 tarek supergroup          0 2018-10-16 13:40 /user/tarek/tizemrane/teragen-output/_SUCCESS
-rw-r--r--   3 tarek supergroup    238.4 M 2018-10-16 13:40 /user/tarek/tizemrane/teragen-output/part-m-00000
-rw-r--r--   3 tarek supergroup    238.4 M 2018-10-16 13:40 /user/tarek/tizemrane/teragen-output/part-m-00001

```
* Copy your partner's file to your target directory 
    * Let one partner use `distCp` on the command line
    * Let the other use BDR

```
## Since the two clusters are note relayed to the same DNS server the communication by distcp is not established because the public IP is translated into a private IP wich is not reconized by the clusters
## We performed a distcp in local between two folders on the same cluster : 
[tarek@n2 ~]$ hadoop distcp hdfs://n2.sebcdomain:8020/user/tarek/tizemrane/teragen-output/* hdfs://n2.sebcdomain:8020/user/tarek/Isalah89/
```
* Browse the results 
    * Use `hdfs fsck <path> -files -blocks` on your source and target directories
    * Copy the work for this lab into `storage/labs/0_replication.md`

```
### Source :
[tarek@n2 ~]$ hdfs fsck /user/tarek/tizemrane -files -blocks
Connecting to namenode via http://n2.sebcdomain:50070/fsck?ugi=tarek&files=1&blocks=1&path=%2Fuser%2Ftarek%2Ftizemrane
FSCK started by tarek (auth:SIMPLE) from /172.31.19.154 for path /user/tarek/tizemrane at Tue Oct 16 17:03:13 UTC 2018
/user/tarek/tizemrane <dir>
/user/tarek/tizemrane/teragen-output <dir>
/user/tarek/tizemrane/teragen-output/_SUCCESS 0 bytes, 0 block(s):  OK

/user/tarek/tizemrane/teragen-output/part-m-00000 250000000 bytes, 2 block(s):  OK
0. BP-43323151-172.31.19.154-1539682168882:blk_1073743827_3003 len=134217728 Live_repl=3
1. BP-43323151-172.31.19.154-1539682168882:blk_1073743830_3006 len=115782272 Live_repl=3

/user/tarek/tizemrane/teragen-output/part-m-00001 250000000 bytes, 2 block(s):  OK
0. BP-43323151-172.31.19.154-1539682168882:blk_1073743828_3004 len=134217728 Live_repl=3
1. BP-43323151-172.31.19.154-1539682168882:blk_1073743829_3005 len=115782272 Live_repl=3

Status: HEALTHY
 Total size:    500000000 B
 Total dirs:    2
 Total files:   3
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 125000000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Tue Oct 16 17:03:13 UTC 2018 in 10 milliseconds


The filesystem under path '/user/tarek/tizemrane' is HEALTHY



### Target 

[tarek@n2 ~]$ hdfs fsck /user/tarek/Isalah89 -files -blocks
Connecting to namenode via http://n2.sebcdomain:50070/fsck?ugi=tarek&files=1&blocks=1&path=%2Fuser%2Ftarek%2FIsalah89
FSCK started by tarek (auth:SIMPLE) from /172.31.19.154 for path /user/tarek/Isalah89 at Tue Oct 16 17:04:00 UTC 2018
/user/tarek/Isalah89 <dir>
/user/tarek/Isalah89/_SUCCESS 0 bytes, 0 block(s):  OK

/user/tarek/Isalah89/part-m-00000 250000000 bytes, 2 block(s):  OK
0. BP-43323151-172.31.19.154-1539682168882:blk_1073744478_3654 len=134217728 Live_repl=3
1. BP-43323151-172.31.19.154-1539682168882:blk_1073744480_3656 len=115782272 Live_repl=3

/user/tarek/Isalah89/part-m-00001 250000000 bytes, 2 block(s):  OK
0. BP-43323151-172.31.19.154-1539682168882:blk_1073744476_3652 len=134217728 Live_repl=3
1. BP-43323151-172.31.19.154-1539682168882:blk_1073744479_3655 len=115782272 Live_repl=3

Status: HEALTHY
 Total size:    500000000 B
 Total dirs:    1
 Total files:   3
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 125000000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          4
 Number of racks:               1
FSCK ended at Tue Oct 16 17:04:00 UTC 2018 in 2 milliseconds


The filesystem under path '/user/tarek/Isalah89' is HEALTHY
```
