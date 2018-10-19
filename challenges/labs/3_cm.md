### hdfs dfs -ls /user

```
[tarek@t1 ~]$ sudo -u hdfs hdfs dfs -ls /user
Found 6 items
drwxr-xr-x   - fullerton hotels          0 2018-10-19 08:33 /user/fullerton
drwxrwxrwx   - mapred    hadoop          0 2018-10-19 08:31 /user/history
drwxrwxr-t   - hive      hive            0 2018-10-19 08:32 /user/hive
drwxrwxr-x   - hue       hue             0 2018-10-19 08:33 /user/hue
drwxrwxr-x   - oozie     oozie           0 2018-10-19 08:33 /user/oozie
drwxr-xr-x   - raffles   shops           0 2018-10-19 08:33 /user/raffles

```

### The output from the CM API call 

```
{
  "items" : [ {
    "hostId" : "636e76ab-e868-43fc-8528-b8fb246391df",
    "ipAddress" : "172.31.22.226",
    "hostname" : "t1.tarekdomain",
    "rackId" : "/default",
    "hostUrl" : "http://t2.tarekdomain:7180/cmf/hostRedirect/636e76ab-e868-43fc-8528-b8fb246391df",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15428349952
  }, {
    "hostId" : "6919dba3-65be-4ef8-945a-a5579af6d39a",
    "ipAddress" : "172.31.21.14",
    "hostname" : "t2.tarekdomain",
    "rackId" : "/default",
    "hostUrl" : "http://t2.tarekdomain:7180/cmf/hostRedirect/6919dba3-65be-4ef8-945a-a5579af6d39a",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15428349952
  }, {
    "hostId" : "6710620e-6412-42c8-834b-9afa4765cc55",
    "ipAddress" : "172.31.18.233",
    "hostname" : "t3.tarekdomain",
    "rackId" : "/default",
    "hostUrl" : "http://t2.tarekdomain:7180/cmf/hostRedirect/6710620e-6412-42c8-834b-9afa4765cc55",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15428349952
  }, {
    "hostId" : "2eece116-0e7f-44de-93bc-7eee00ab9c66",
    "ipAddress" : "172.31.20.152",
    "hostname" : "t4.tarekdomain",
    "rackId" : "/default",
    "hostUrl" : "http://t2.tarekdomain:7180/cmf/hostRedirect/2eece116-0e7f-44de-93bc-7eee00ab9c66",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15428349952
  }, {
    "hostId" : "0965b8e3-71b4-460e-ab54-ec4356c7256e",
    "ipAddress" : "172.31.18.190",
    "hostname" : "t5.tarekdomain",
    "rackId" : "/default",
    "hostUrl" : "http://t2.tarekdomain:7180/cmf/hostRedirect/0965b8e3-71b4-460e-ab54-ec4356c7256e",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15428349952
  } ]
}
```

