```
## stop Hive service
curl -X POST -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/v2/clusters/tizemrane/services/hive/commands/stop'
{
  "id" : 802,
  "name" : "Stop",
  "startTime" : "2018-10-17T10:26:04.480Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}

## start hive service
curl -X POST -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/v2/clusters/tizemrane/services/hive/commands/start'
{
  "id" : 806,
  "name" : "Start",
  "startTime" : "2018-10-17T10:27:27.314Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}              

## check hive service
curl -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/v2/clusters/tizemrane/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://n1.sebcdomain:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false,
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive"
}

```