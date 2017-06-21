
#1.Report the latest available version of the API
```
[root@feng-xu-1 cm]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.com:7180/api/version'
v15
```

#2.Report the CM version
```
[root@feng-xu-1 cm]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.com:7180/api/v15/cm/version'
{
  "version" : "5.10.1",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170319-2001",
  "gitHash" : "f226435f6fa5f545543c00245900ae43bea7a29c",
  "snapshot" : false
}
```

#3.List all CM users
```
[root@feng-xu-1 cm]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.cm:7180/api/v15/users'
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "fx185000",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```

#4.Report the database server in use by CM
```
[root@feng-xu-1 cm]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.cm:7180/api/v15/cm/scmDbInfo'
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```