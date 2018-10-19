### Teragen Command

```
[raffles@t1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -D mapreduce.job.maps=6 -D dfs.blocksize=32M  51200000 tgen512
```

### Time Output

```
real    1m16.744s
user    0m9.354s
sys     0m2.039s

```

### hdfs dfs -ls /user/raffles/tgen512

```
[raffles@t1 ~]$ hdfs dfs -ls /user/raffles/tgen512
Found 7 items
-rw-r--r--   3 raffles shops          0 2018-10-19 08:46 /user/raffles/tgen512/_SUCCESS
-rw-r--r--   3 raffles shops  853333400 2018-10-19 08:46 /user/raffles/tgen512/part-m-00000
-rw-r--r--   3 raffles shops  853333300 2018-10-19 08:46 /user/raffles/tgen512/part-m-00001
-rw-r--r--   3 raffles shops  853333300 2018-10-19 08:46 /user/raffles/tgen512/part-m-00002
-rw-r--r--   3 raffles shops  853333400 2018-10-19 08:46 /user/raffles/tgen512/part-m-00003
-rw-r--r--   3 raffles shops  853333300 2018-10-19 08:46 /user/raffles/tgen512/part-m-00004
-rw-r--r--   3 raffles shops  853333300 2018-10-19 08:46 /user/raffles/tgen512/part-m-00005

```

### Blocks

```
[raffles@t1 ~]$ hdfs fsck /user/raffles/tgen512 -blocks | grep "Total blocks"
Connecting to namenode via http://t3.tarekdomain:50070/fsck?ugi=raffles&blocks=1&path=%2Fuser%2Fraffles%2Ftgen512
 Total blocks (validated):      156 (avg. block size 32820512 B)
```