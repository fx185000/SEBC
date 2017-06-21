#1. stop hive service
```
[root@feng-xu-1 process]# curl -X POST -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.com:7180/api/v14/clusters/cluster/services/hive/commands/stop'
{
  "id" : 433,
  "name" : "Stop",
  "startTime" : "2017-06-21T18:06:17.535Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

#2. check hive stop result
```
[root@feng-xu-1 process]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudra.com:7180/api/v14/commands/433'
{
  "id" : 433,
  "name" : "Stop",
  "startTime" : "2017-06-21T18:06:17.535Z",
  "endTime" : "2017-06-21T18:06:21.238Z",
  "active" : false,
  "success" : true,
  "resultMessage" : "Successfully stopped service.",
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  },
  "children" : {
    "items" : [ {
      "id" : 435,
      "name" : "Stop",
      "startTime" : "2017-06-21T18:06:17.540Z",
      "endTime" : "2017-06-21T18:06:21.238Z",
      "active" : false,
      "success" : true,
      "resultMessage" : "Successfully stopped process.",
      "serviceRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive"
      },
      "roleRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive",
        "roleName" : "hive-HIVEMETASTORE-b3816d202d81ada101b80d98fea158bb"
      }
    }, {
      "id" : 434,
      "name" : "Stop",
      "startTime" : "2017-06-21T18:06:17.537Z",
      "endTime" : "2017-06-21T18:06:21.229Z",
      "active" : false,
      "success" : true,
      "resultMessage" : "Successfully stopped process.",
      "serviceRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive"
      },
      "roleRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive",
        "roleName" : "hive-HIVESERVER2-b3816d202d81ada101b80d98fea158bb"
      }
    } ]
  },
  "canRetry" : false
}
```

#3.start hive service
```
[root@feng-xu-1 process]# curl -X POST -u fx185000:cloudera 'http://feng-xu-1.vc.cloudera.com:7180/api/v14/clusters/cluster/services/hive/commands/start'
{
  "id" : 437,
  "name" : "Start",
  "startTime" : "2017-06-21T18:07:52.446Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```

#4.check hive start result
```
[root@feng-xu-1 process]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.com:7180/api/v14/commands/437'
{
  "id" : 437,
  "name" : "Start",
  "startTime" : "2017-06-21T18:07:52.446Z",
  "endTime" : "2017-06-21T18:08:14.909Z",
  "active" : false,
  "success" : true,
  "resultMessage" : "Successfully started service.",
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  },
  "children" : {
    "items" : [ {
      "id" : 439,
      "name" : "Start",
      "startTime" : "2017-06-21T18:07:52.530Z",
      "endTime" : "2017-06-21T18:08:14.905Z",
      "active" : false,
      "success" : true,
      "resultMessage" : "Successfully started process.",
      "serviceRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive"
      },
      "roleRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive",
        "roleName" : "hive-HIVEMETASTORE-b3816d202d81ada101b80d98fea158bb"
      }
    }, {
      "id" : 438,
      "name" : "Start",
      "startTime" : "2017-06-21T18:07:52.467Z",
      "endTime" : "2017-06-21T18:08:14.897Z",
      "active" : false,
      "success" : true,
      "resultMessage" : "Successfully started process.",
      "serviceRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive"
      },
      "roleRef" : {
        "clusterName" : "cluster",
        "serviceName" : "hive",
        "roleName" : "hive-HIVESERVER2-b3816d202d81ada101b80d98fea158bb"
      }
    } ]
  },
  "canRetry" : false
}
```
#5.check the current state of hive service
```
[root@feng-xu-1 process]# curl -u fx185000:cloudera 'http://feng-xu-1.vpc.cloudera.com:7180/api/v14/clusters/cluster/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://feng-xu-1.vpc.cloudera.com:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://feng-xu-1.vpc.cloudera.com:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "GOOD_HEALTH"
}
```
