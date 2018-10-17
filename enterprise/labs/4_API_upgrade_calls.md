```

## the latest available version of the API
curl -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/version'
v19

## the CM version 

curl -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/v19/cm/version'
{
  "version" : "5.14.4",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20180707-0439",
  "gitHash" : "0971e84bdceb60db9b96533f46451f40ed8cbdf9",
  "snapshot" : false
}

## List all CM users

curl -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/v19/users'   {
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  }, {
    "name" : "tizemrane",
    "roles" : [ "ROLE_ADMIN" ]
  } ]
}

## the database server in use by CM

curl -u tizemrane:cloudera 'http://ec2-18-184-160-216.eu-central-1.compute.amazonaws.com:7180/api/v19/cm/scmDbInfo'
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```