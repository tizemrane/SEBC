### Terasort

```
[raffles@t1 ~]$ kinit raffles
Password for raffles@TIZEMRANE.SG:
[raffles@t1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort -Dmapreduce.job.maps=40 -Dmapreduce.job.reduces=10 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 -Dmapreduce.reduce.memory.mb=1024 -Dmapreduce.reduce.java.opts.max.heap=819  -Dmapreduce.input.fileinputformat.split.minsize=134217728 -Dmapreduce.input.fileinputformat.split.maxsize=134217728  tgen512 tsort512
18/10/19 09:18:49 INFO terasort.TeraSort: starting
18/10/19 09:18:52 INFO hdfs.DFSClient: Created token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@TIZEMRANE.SG, renewer=yarn, realUser=, issueDate=1539940732005, maxDate=1540545532005, sequenceNumber=1, masterKeyId=2 on 172.31.18.233:8020
18/10/19 09:18:52 INFO security.TokenCache: Got dt for hdfs://t3.tarekdomain:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.18.233:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@TIZEMRANE.SG, renewer=yarn, realUser=, issueDate=1539940732005, maxDate=1540545532005, sequenceNumber=1, masterKeyId=2)
18/10/19 09:18:52 INFO input.FileInputFormat: Total input paths to process : 6
Spent 628ms computing base-splits.
Spent 5ms computing TeraScheduler splits.
Computing input splits took 635ms
Sampling 10 splits of 42
Making 10 from 100000 sampled records
Computing parititions took 937ms
Spent 1574ms computing partitions.
18/10/19 09:18:53 INFO client.RMProxy: Connecting to ResourceManager at t1.tarekdomain/172.31.22.226:8032
18/10/19 09:18:53 INFO mapreduce.JobSubmitter: number of splits:42
18/10/19 09:18:54 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539940583077_0001
18/10/19 09:18:54 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.18.233:8020, Ident: (token for raffles: HDFS_DELEGATION_TOKEN owner=raffles@TIZEMRANE.SG, renewer=yarn, realUser=, issueDate=1539940732005, maxDate=1540545532005, sequenceNumber=1, masterKeyId=2)
18/10/19 09:18:55 INFO impl.YarnClientImpl: Submitted application application_1539940583077_0001
18/10/19 09:18:55 INFO mapreduce.Job: The url to track the job: http://t1.tarekdomain:8088/proxy/application_1539940583077_0001/
18/10/19 09:18:55 INFO mapreduce.Job: Running job: job_1539940583077_0001
18/10/19 09:19:09 INFO mapreduce.Job: Job job_1539940583077_0001 running in uber mode : false
18/10/19 09:19:09 INFO mapreduce.Job:  map 0% reduce 0%
18/10/19 09:19:31 INFO mapreduce.Job:  map 5% reduce 0%
18/10/19 09:19:41 INFO mapreduce.Job:  map 7% reduce 0%
18/10/19 09:19:42 INFO mapreduce.Job:  map 24% reduce 0%
18/10/19 09:19:45 INFO mapreduce.Job:  map 29% reduce 0%
18/10/19 09:19:57 INFO mapreduce.Job:  map 33% reduce 0%
18/10/19 09:20:02 INFO mapreduce.Job:  map 40% reduce 0%
18/10/19 09:20:03 INFO mapreduce.Job:  map 48% reduce 0%
18/10/19 09:20:04 INFO mapreduce.Job:  map 52% reduce 0%
18/10/19 09:20:11 INFO mapreduce.Job:  map 57% reduce 0%
18/10/19 09:20:24 INFO mapreduce.Job:  map 68% reduce 0%
18/10/19 09:20:25 INFO mapreduce.Job:  map 76% reduce 0%
18/10/19 09:20:26 INFO mapreduce.Job:  map 81% reduce 0%
18/10/19 09:20:33 INFO mapreduce.Job:  map 86% reduce 0%
18/10/19 09:20:41 INFO mapreduce.Job:  map 93% reduce 0%
18/10/19 09:20:42 INFO mapreduce.Job:  map 95% reduce 0%
18/10/19 09:20:46 INFO mapreduce.Job:  map 97% reduce 0%
18/10/19 09:20:47 INFO mapreduce.Job:  map 98% reduce 0%
18/10/19 09:20:48 INFO mapreduce.Job:  map 99% reduce 0%
18/10/19 09:20:49 INFO mapreduce.Job:  map 100% reduce 3%
18/10/19 09:20:50 INFO mapreduce.Job:  map 100% reduce 7%
18/10/19 09:20:52 INFO mapreduce.Job:  map 100% reduce 20%
18/10/19 09:20:56 INFO mapreduce.Job:  map 100% reduce 27%
18/10/19 09:20:58 INFO mapreduce.Job:  map 100% reduce 29%
18/10/19 09:21:02 INFO mapreduce.Job:  map 100% reduce 30%
18/10/19 09:21:03 INFO mapreduce.Job:  map 100% reduce 38%
18/10/19 09:21:04 INFO mapreduce.Job:  map 100% reduce 46%
18/10/19 09:21:05 INFO mapreduce.Job:  map 100% reduce 50%
18/10/19 09:21:06 INFO mapreduce.Job:  map 100% reduce 51%
18/10/19 09:21:08 INFO mapreduce.Job:  map 100% reduce 52%
18/10/19 09:21:09 INFO mapreduce.Job:  map 100% reduce 59%
18/10/19 09:21:10 INFO mapreduce.Job:  map 100% reduce 62%
18/10/19 09:21:11 INFO mapreduce.Job:  map 100% reduce 64%
18/10/19 09:21:13 INFO mapreduce.Job:  map 100% reduce 67%
18/10/19 09:21:14 INFO mapreduce.Job:  map 100% reduce 72%
18/10/19 09:21:15 INFO mapreduce.Job:  map 100% reduce 75%
18/10/19 09:21:16 INFO mapreduce.Job:  map 100% reduce 76%
18/10/19 09:21:18 INFO mapreduce.Job:  map 100% reduce 77%
18/10/19 09:21:19 INFO mapreduce.Job:  map 100% reduce 80%
18/10/19 09:21:20 INFO mapreduce.Job:  map 100% reduce 83%
18/10/19 09:21:21 INFO mapreduce.Job:  map 100% reduce 85%
18/10/19 09:21:22 INFO mapreduce.Job:  map 100% reduce 86%
18/10/19 09:21:23 INFO mapreduce.Job:  map 100% reduce 87%
18/10/19 09:21:25 INFO mapreduce.Job:  map 100% reduce 89%
18/10/19 09:21:26 INFO mapreduce.Job:  map 100% reduce 91%
18/10/19 09:21:28 INFO mapreduce.Job:  map 100% reduce 92%
18/10/19 09:21:29 INFO mapreduce.Job:  map 100% reduce 94%
18/10/19 09:21:30 INFO mapreduce.Job:  map 100% reduce 96%
18/10/19 09:21:32 INFO mapreduce.Job:  map 100% reduce 97%
18/10/19 09:21:33 INFO mapreduce.Job:  map 100% reduce 98%
18/10/19 09:21:37 INFO mapreduce.Job:  map 100% reduce 100%
18/10/19 09:21:38 INFO mapreduce.Job: Job job_1539940583077_0001 completed successfully
18/10/19 09:21:39 INFO mapreduce.Job: Counters: 50
        File System Counters
                FILE: Number of bytes read=2289594426
                FILE: Number of bytes written=4551477292
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=5120005250
                HDFS: Number of bytes written=5120000000
                HDFS: Number of read operations=156
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=20
        Job Counters
                Launched map tasks=42
                Launched reduce tasks=10
                Data-local map tasks=40
                Rack-local map tasks=2
                Total time spent by all maps in occupied slots (ms)=813462
                Total time spent by all reduces in occupied slots (ms)=443242
                Total time spent by all map tasks (ms)=813462
                Total time spent by all reduce tasks (ms)=443242
                Total vcore-milliseconds taken by all map tasks=813462
                Total vcore-milliseconds taken by all reduce tasks=443242
                Total megabyte-milliseconds taken by all map tasks=832985088
                Total megabyte-milliseconds taken by all reduce tasks=453879808
        Map-Reduce Framework
                Map input records=51200000
                Map output records=51200000
                Map output bytes=5222400000
                Map output materialized bytes=2253977434
                Input split bytes=5250
                Combine input records=0
                Combine output records=0
                Reduce input groups=51200000
                Reduce shuffle bytes=2253977434
                Reduce input records=51200000
                Reduce output records=51200000
                Spilled Records=102400000
                Shuffled Maps =420
                Failed Shuffles=0
                Merged Map outputs=420
                GC time elapsed (ms)=30050
                CPU time spent (ms)=695560
                Physical memory (bytes) snapshot=30998192128
                Virtual memory (bytes) snapshot=144745549824
                Total committed heap usage (bytes)=30328487936
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=5120000000
        File Output Format Counters
                Bytes Written=5120000000
18/10/19 09:21:39 INFO terasort.TeraSort: done

real    2m50.908s
user    0m12.106s
sys     0m2.394s


```

