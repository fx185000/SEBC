#1.The command and output for hdfs dfs -ls /user
```
[hdfs@fx185000-1 ~]$ hdfs dfs -ls /user
Found 7 items
drwxrwxr-x   - haley  comets           0 2017-06-23 10:58 /user/haley
drwxrwxrwx   - mapred hadoop           0 2017-06-23 10:52 /user/history
drwxrwxr-t   - hive   hive             0 2017-06-23 10:53 /user/hive
drwxrwxr-x   - hue    hue              0 2017-06-23 10:54 /user/hue
drwxrwxr-x   - oozie  oozie            0 2017-06-23 10:54 /user/oozie
drwxrwxr-x   - saturn planets          0 2017-06-23 10:57 /user/saturn
drwxr-x--x   - spark  spark            0 2017-06-23 10:52 /user/spark
```

#2.The command and output from the CM API call ../api/v14/hosts
```
[hdfs@fx185000-1 ~]$ curl -u admin:admin 'http://fx185000-2.vpc.cloudera.com:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "88723c8f-0475-46af-a071-5f0336a32359",
    "ipAddress" : "172.28.199.152",
    "hostname" : "fx185000-1.vpc.cloudera.com",
    "rackId" : "/default",
    "hostUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/hostRedirect/88723c8f-0475-46af-a071-5f0336a32359",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15604989952
  }, {
    "hostId" : "35c551ff-9e5f-4baf-a468-9a439de09b35",
    "ipAddress" : "172.28.194.140",
    "hostname" : "fx185000-2.vpc.cloudera.com",
    "rackId" : "/default",
    "hostUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/hostRedirect/35c551ff-9e5f-4baf-a468-9a439de09b35",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15604989952
  }, {
    "hostId" : "35f97d9d-75be-4c27-99de-cf8fccad6c82",
    "ipAddress" : "172.28.196.102",
    "hostname" : "fx185000-3.vpc.cloudera.com",
    "rackId" : "/default",
    "hostUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/hostRedirect/35f97d9d-75be-4c27-99de-cf8fccad6c82",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15604989952
  }, {
    "hostId" : "f6f184e8-cc38-4236-affb-21fb3deb203d",
    "ipAddress" : "172.28.197.187",
    "hostname" : "fx185000-4.vpc.cloudera.com",
    "rackId" : "/default",
    "hostUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/hostRedirect/f6f184e8-cc38-4236-affb-21fb3deb203d",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15604989952
  }, {
    "hostId" : "cfb5866b-13c0-4101-bc05-81e591ce160b",
    "ipAddress" : "172.28.192.90",
    "hostname" : "fx185000-5.vpc.cloudera.com",
    "rackId" : "/default",
    "hostUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/hostRedirect/cfb5866b-13c0-4101-bc05-81e591ce160b",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 15604989952
  } ]
 }
  ```

#3.The command and output from the CM API call ../api/v8/clusters/<githubName>/services
```
[hdfs@fx185000-1 ~]$ curl -u admin:admin 'http://fx185000-2.vpc.cloudera.com:710/api/v6/clusters/fx185000/services'
{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "spark_on_yarn",
    "type" : "SPARK_ON_YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/spark_on_yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Spark"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://fx185000-2.vpc.cloudera.com:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]
}
```