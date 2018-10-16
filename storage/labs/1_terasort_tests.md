## <center> HDFS Lab: Test HDFS performance

* Create an end-user Linux account named with your GitHub handle
    * Create a home HDFS directory for this user as well
    * Run the following exercises as this user
```
[tarek@n2 ~]$ sudo su -
[root@n2 ~]# cd /home
[root@n2 home]# useradd tizemrane
[root@n2 home]# passwd tizemrane
Changing password for user tizemrane.
New password:
Retype new password:
[root@n2 home]# sudo -u hdfs hdfs dfs -mkdir /user/tizemrane
[root@n2 home]# sudo -u hdfs hdfs dfs -chown tizemrane:tizemrane /user/tizemrane

```
* Create a 10 GB file using `teragen`
    * Set the number of mappers to four
    * Limit the block size to 32 MB 
    * Land the result under your user's home directory
    * Use the `time` command to report the job's duration
```
[tizemrane@n2 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -D mapreduce.job.maps=4  -D dfs.blocksize=32M 100000000 teragen-output
...
real    2m23.154s
user    0m11.832s
sys     0m2.073s
```

* Run the `terasort` command on this file 
    * Use the `time` command to report the job's duration
    * Land the result under your user's home directory

```
[tizemrane@n2 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapred.map.tasks.speculative.execution=false teragen-output terasort_out

real    17m25.294s
user    0m18.543s
sys     0m2.854s

```
* Report your work in `storage/labs/1_terasort_tests.md`, including:
    * The full `teragen` and `terasort` commands you used 
    * The `time` result of each job 
