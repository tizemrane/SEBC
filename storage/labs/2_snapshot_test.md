
List the commands and output for each step below in `storage/labs/2_snapshot_test.md`.

* Create a `precious` directory in HDFS; copy the ZIP course file into it.
```
[tarek@n3 ~]$ hdfs dfs -mkdir precious
[tarek@n3 ~]$ hdfs dfs -put SEBC-master.zip precious
```
* Enable snapshots for `precious`
* Create a snapshot called `sebc-hdfs-test`
```
## from cloudera manager : 
hdfs/hdfs.sh ["dfsadmin","-allowSnapshot","/user/tarek/precious"]
hdfs/hdfs.sh ["dfs","-createSnapshot","/user/tarek/precious","sebc-hdfs-test"]
```
* Delete the directory
* Delete the ZIP file
* Restore the deleted file 
```
[tarek@n3 ~]$ hdfs dfs -rm -r  /user/tarek/precious
rm: Failed to move to trash: hdfs://n2.sebcdomain:8020/user/tarek/precious: The directory /user/tarek/precious cannot be deleted since /user/tarek/precious is snapshottable and already has snapshots
[tarek@n3 ~]$ hdfs dfs -rm -r  /user/tarek/precious/SEBC-master.zip
18/10/16 15:59:10 INFO fs.TrashPolicyDefault: Moved: 'hdfs://n2.sebcdomain:8020/user/tarek/precious/SEBC-master.zip' to trash at: hdfs://n2.sebcdomain:8020/user/tarek/.Trash/Current/user/tarek/precious/SEBC-master.zip
## depuis Cloudera Manager :
hdfs/hdfs.sh ["dfs","-cp","/user/tarek/precious/.snapshot/sebc-hdfs-test","/user/tarek/.snapshot_sebc-hdfs-test_bbfa0f07-5a6d-4dd7-abbe-f51e0d5116fe"]

hdfs/hdfs.sh ["dfs","-mv","/user/tarek/.snapshot_sebc-hdfs-test_bbfa0f07-5a6d-4dd7-abbe-f51e0d5116fe/*","/user/tarek/precious"]

hdfs/hdfs.sh ["dfs","-rm","-r","/user/tarek/.snapshot_sebc-hdfs-test_bbfa0f07-5a6d-4dd7-abbe-f51e0d5116fe"]
```

* Capture the NameNode web UI screen that lists snapshots in `storage/labs/2_snapshot_list.png`.