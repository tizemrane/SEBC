<div style="page-break-after: always;"></div>

## <center> CM Monitoring Lab

_Use CM to answer the following questions. For some questions, search will help you. Watch out for trick questions! (Some of these questions have been asked by customers.)  Put the questions and their answers in the file_ `enterprise/labs/0_CM_treasure_hunt.md`

* What is ubertask optimization?
 => it enable to  runs "sufficiently small" jobs sequentially within a single JVM. "Small" is defined by the mapreduce.job.ubertask.maxmaps, mapreduce.job.ubertask.maxreduces, and mapreduce.job.ubertask.maxbytes settings.
* Where in CM is the Kerberos Security Realm value displayed?
 => Administration > Settings, parameter : "default_realm"
* Which CDH service(s) host a property for enabling Kerberos authentication?
 => Zookeeper
* How do you upgrade the CM agents?
 => We need first to upgrade the Cloudera Manager Server 
 => then to upgrade the agents,there are two options :
  1. By using Cloudera Manager : https://CM_url:CM_port/cmf/upgrade-wizard/welcome
  2. By using Command Line : on each host, update the cloudera-manager.repo, stop the agent cloudera-scm-agent, upgrade cloudera-manager-daemons cloudera-manager-agent via yum then start the agent and finally Run the Run Host Inspector on Cloudera manager interface
 
* Give the `tsquery` statement used to chart Hue's CPU utilization?
```
select cpu_percent where roleType=HUE_SERVER 
```
* Name all the roles that make up the Hive service\
    Gateway\
    WHCS  WebHCat Server\
    HMS  Hive Metastore Server\
    HS2  HiveServer2

* What steps must be completed before integrating Cloudera Manager with Kerberos?
    - Set up a working KDC. Cloudera Manager supports authentication with MIT KDC and Active Directory.
     For Hue and Oozie, the Kerberos realm must support renewable tickets.
    - Install Kerberos client OS-specific packages on all cluster hosts and client hosts that will authenticate using Kerberos.
    - Create an account for Cloudera Manager that has the permissions to create other accounts in the KDC. 
