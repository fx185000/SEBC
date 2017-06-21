```
{
  "timestamp" : "2017-06-21T17:48:34.300Z",
  "clusters" : [ {
    "name" : "cluster",
    "displayName" : "fx185000",
    "version" : "CDH5",
    "fullVersion" : "5.9.1",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "feng-xu-1.vpc.cloudera.com",
          "sensitive" : false
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "Root123~",
          "sensitive" : true
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn",
          "sensitive" : false
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper",
          "sensitive" : false
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-027479cad823500c7dbfe56959071872",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-b3816d202d81ada101b80d98fea158bb",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-bb0ee424451456a674cdbfbf77990c2c",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "9e6be5c9-ee1c-4843-9b51-442dff82fb50"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-d0e65c30524c315cc10b5a88c7d065b5",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "2466595c-00c7-41ec-9981-e0dc2896596a"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-GATEWAY-fddb96f5913b76d85f32940399da2f40",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "87bd4519-f38e-466e-ac61-bdf13b693137"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-GATEWAY-BASE"
        }
      }, {
        "name" : "hive-HIVEMETASTORE-b3816d202d81ada101b80d98fea158bb",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "eb3ia7llkvhot1u7hbo05aaga",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVEMETASTORE-BASE"
        }
      }, {
        "name" : "hive-HIVESERVER2-b3816d202d81ada101b80d98fea158bb",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cez2oa7n0b7qc69t1yuy4225u",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hive-HIVESERVER2-BASE"
        }
      } ],
      "displayName" : "Hive",
      "roleConfigGroups" : [ {
        "name" : "hive-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-BASE",
        "displayName" : "Hive Metastore Server Default Group",
        "roleType" : "HIVEMETASTORE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-BASE",
        "displayName" : "HiveServer2 Default Group",
        "roleType" : "HIVESERVER2",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641",
            "sensitive" : false
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4",
            "sensitive" : false
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "4160539852",
            "sensitive" : false
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102",
            "sensitive" : false
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "700",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hive-WEBHCAT-BASE",
        "displayName" : "WebHCat Server Default Group",
        "roleType" : "WEBHCAT",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hive"
        },
        "config" : {
          "items" : [ ]
        }
      } ],
      "replicationSchedules" : [ ]
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-027479cad823500c7dbfe56959071872",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "es9hncbsku24la3ysrsrcxmvf",
            "sensitive" : true
          }, {
            "name" : "serverId",
            "value" : "2",
            "sensitive" : false
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      }, {
        "name" : "zookeeper-SERVER-b3816d202d81ada101b80d98fea158bb",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7h1de17630x3sirp2yj0y2qwb",
            "sensitive" : true
          }, {
            "name" : "serverId",
            "value" : "1",
            "sensitive" : false
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      }, {
        "name" : "zookeeper-SERVER-bb0ee424451456a674cdbfbf77990c2c",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "9e6be5c9-ee1c-4843-9b51-442dff82fb50"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9ob927nx0odivm6vu5mm28dny",
            "sensitive" : true
          }, {
            "name" : "serverId",
            "value" : "3",
            "sensitive" : false
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "zookeeper-SERVER-BASE"
        }
      } ],
      "displayName" : "ZooKeeper",
      "roleConfigGroups" : [ {
        "name" : "zookeeper-SERVER-BASE",
        "displayName" : "Server Default Group",
        "roleType" : "SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "zookeeper"
        },
        "config" : {
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      } ]
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "items" : [ {
          "name" : "database_host",
          "value" : "feng-xu-1.vpc.cloudera.com",
          "sensitive" : false
        }, {
          "name" : "database_password",
          "value" : "Root123~",
          "sensitive" : true
        }, {
          "name" : "database_type",
          "value" : "mysql",
          "sensitive" : false
        }, {
          "name" : "hive_service",
          "value" : "hive",
          "sensitive" : false
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-NAMENODE-b3816d202d81ada101b80d98fea158bb",
          "sensitive" : false
        }, {
          "name" : "oozie_service",
          "value" : "oozie",
          "sensitive" : false
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper",
          "sensitive" : false
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-b3816d202d81ada101b80d98fea158bb",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "39ui2hdg8sqtomxnuf5isns9s",
            "sensitive" : true
          }, {
            "name" : "secret_key",
            "value" : "oy5RPjJUhGuQiz92WN3tAw7DAn9faz",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hue-HUE_SERVER-BASE"
        }
      } ],
      "displayName" : "Hue",
      "roleConfigGroups" : [ {
        "name" : "hue-HUE_LOAD_BALANCER-BASE",
        "displayName" : "Load Balancer Default Group",
        "roleType" : "HUE_LOAD_BALANCER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hue-HUE_SERVER-BASE",
        "displayName" : "Hue Server Default Group",
        "roleType" : "HUE_SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hue-KT_RENEWER-BASE",
        "displayName" : "Kerberos Ticket Renewer Default Group",
        "roleType" : "KT_RENEWER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hue"
        },
        "config" : {
          "items" : [ ]
        }
      } ]
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive",
          "sensitive" : false
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn",
          "sensitive" : false
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper",
          "sensitive" : false
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-b3816d202d81ada101b80d98fea158bb",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bs6k8lde1ktr1enmmatsag4uv",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "oozie-OOZIE_SERVER-BASE"
        }
      } ],
      "displayName" : "Oozie",
      "roleConfigGroups" : [ {
        "name" : "oozie-OOZIE_SERVER-BASE",
        "displayName" : "Oozie Server Default Group",
        "roleType" : "OOZIE_SERVER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "oozie"
        },
        "config" : {
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "feng-xu-1.vpc.cloudera.com",
            "sensitive" : false
          }, {
            "name" : "oozie_database_password",
            "value" : "Root123~",
            "sensitive" : true
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql",
            "sensitive" : false
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie",
            "sensitive" : false
          }, {
            "name" : "oozie_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      } ]
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs",
          "sensitive" : false
        }, {
          "name" : "rm_dirty",
          "value" : "false",
          "sensitive" : false
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "80",
          "sensitive" : false
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false",
          "sensitive" : false
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false",
          "sensitive" : false
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "Jgms0KnnkKjOneugkjGqSwZQGAnjIJ",
          "sensitive" : true
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper",
          "sensitive" : false
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-b3816d202d81ada101b80d98fea158bb",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "crgbfpufua4pc8sa8cqokxb16",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-JOBHISTORY-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-027479cad823500c7dbfe56959071872",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1pt4rib857hwdvi0srwyl4185",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-1"
        }
      }, {
        "name" : "yarn-NODEMANAGER-bb0ee424451456a674cdbfbf77990c2c",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "9e6be5c9-ee1c-4843-9b51-442dff82fb50"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bay80c216yvypleewwzcypqg7",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-1"
        }
      }, {
        "name" : "yarn-NODEMANAGER-d0e65c30524c315cc10b5a88c7d065b5",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "2466595c-00c7-41ec-9981-e0dc2896596a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7bylvtrjrzuinjqtpmi1xjk7l",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-NODEMANAGER-fddb96f5913b76d85f32940399da2f40",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "87bd4519-f38e-466e-ac61-bdf13b693137"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8v84goyw2t2wvprz0suk6a68t",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-NODEMANAGER-BASE"
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-b3816d202d81ada101b80d98fea158bb",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "53",
            "sensitive" : false
          }, {
            "name" : "role_jceks_password",
            "value" : "ajao570bt910i596ihza129xj",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "yarn-RESOURCEMANAGER-BASE"
        }
      } ],
      "displayName" : "YARN (MR2 Included)",
      "roleConfigGroups" : [ {
        "name" : "yarn-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8",
            "sensitive" : false
          }, {
            "name" : "mapred_submit_replication",
            "value" : "2",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "yarn-JOBHISTORY-BASE",
        "displayName" : "JobHistory Server Default Group",
        "roleType" : "JOBHISTORY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1",
        "displayName" : "NodeManager Group 1",
        "roleType" : "NODEMANAGER",
        "base" : false,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1600",
            "sensitive" : false
          }, {
            "name" : "rm_io_weight",
            "value" : "800",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "3366",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-BASE",
        "displayName" : "NodeManager Default Group",
        "roleType" : "NODEMANAGER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4",
            "sensitive" : false
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "5999",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-BASE",
        "displayName" : "ResourceManager Default Group",
        "roleType" : "RESOURCEMANAGER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "yarn"
        },
        "config" : {
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "5999",
            "sensitive" : false
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3",
            "sensitive" : false
          } ]
        }
      } ]
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "V8sqGnC2lVmbvjpJLhuqs4ONHZnSuZ",
          "sensitive" : true
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)",
          "sensitive" : false
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "3mf4ik4wErFhhtXIRrmqCz2vehbvFN",
          "sensitive" : true
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "tZOpW7TkAeIXyFH51QaQqQynFYjVaa",
          "sensitive" : true
        }, {
          "name" : "rm_dirty",
          "value" : "false",
          "sensitive" : false
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "20",
          "sensitive" : false
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper",
          "sensitive" : false
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-b3816d202d81ada101b80d98fea158bb",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-BALANCER-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-027479cad823500c7dbfe56959071872",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7db6ovpyd9w8myz5bcq7hpcmx",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-bb0ee424451456a674cdbfbf77990c2c",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "9e6be5c9-ee1c-4843-9b51-442dff82fb50"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5futabpofv0aeh42g0z4i6pbs",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-d0e65c30524c315cc10b5a88c7d065b5",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "2466595c-00c7-41ec-9981-e0dc2896596a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "c62ebkzkii4iq38eedfvkql0u",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-DATANODE-fddb96f5913b76d85f32940399da2f40",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "87bd4519-f38e-466e-ac61-bdf13b693137"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4rrani8sumxglzl5lf91rrv68",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-DATANODE-BASE"
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-027479cad823500c7dbfe56959071872",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7qijxhtk47mqavktyqkmyagz7",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-FAILOVERCONTROLLER-BASE"
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-b3816d202d81ada101b80d98fea158bb",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cyho1ig3c8x8uyzgohq5ne4d6",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-FAILOVERCONTROLLER-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-027479cad823500c7dbfe56959071872",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5f5ntvjxvsz32v0dgmt7fkhwz",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-b3816d202d81ada101b80d98fea158bb",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "4wx4b39q2kf9zfsn8mx4wbo7n",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-JOURNALNODE-bb0ee424451456a674cdbfbf77990c2c",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "9e6be5c9-ee1c-4843-9b51-442dff82fb50"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "59nc2gjnbohsmb37vsh46st2d",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-JOURNALNODE-BASE"
        }
      }, {
        "name" : "hdfs-NAMENODE-027479cad823500c7dbfe56959071872",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true",
            "sensitive" : false
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1",
            "sensitive" : false
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1",
            "sensitive" : false
          }, {
            "name" : "namenode_id",
            "value" : "61",
            "sensitive" : false
          }, {
            "name" : "role_jceks_password",
            "value" : "awkuipeequ7viifeg66rvyx2n",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-NAMENODE-BASE"
        }
      }, {
        "name" : "hdfs-NAMENODE-b3816d202d81ada101b80d98fea158bb",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true",
            "sensitive" : false
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "nameservice1",
            "sensitive" : false
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "nameservice1",
            "sensitive" : false
          }, {
            "name" : "namenode_id",
            "value" : "55",
            "sensitive" : false
          }, {
            "name" : "role_jceks_password",
            "value" : "be43zjlc8yhjyknb4pwi81qo0",
            "sensitive" : true
          } ]
        },
        "roleConfigGroupRef" : {
          "roleConfigGroupName" : "hdfs-NAMENODE-BASE"
        }
      } ],
      "displayName" : "HDFS",
      "roleConfigGroups" : [ {
        "name" : "hdfs-BALANCER-BASE",
        "displayName" : "Balancer Default Group",
        "roleType" : "BALANCER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-BASE",
        "displayName" : "DataNode Default Group",
        "roleType" : "DATANODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824",
            "sensitive" : false
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn",
            "sensitive" : false
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296",
            "sensitive" : false
          }, {
            "name" : "rm_cpu_shares",
            "value" : "400",
            "sensitive" : false
          }, {
            "name" : "rm_io_weight",
            "value" : "200",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-BASE",
        "displayName" : "Failover Controller Default Group",
        "roleType" : "FAILOVERCONTROLLER",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-GATEWAY-BASE",
        "displayName" : "Gateway Default Group",
        "roleType" : "GATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-BASE",
        "displayName" : "HttpFS Default Group",
        "roleType" : "HTTPFS",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-BASE",
        "displayName" : "JournalNode Default Group",
        "roleType" : "JOURNALNODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-BASE",
        "displayName" : "NameNode Default Group",
        "roleType" : "NAMENODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn",
            "sensitive" : false
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022",
            "sensitive" : false
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      }, {
        "name" : "hdfs-NFSGATEWAY-BASE",
        "displayName" : "NFS Gateway Default Group",
        "roleType" : "NFSGATEWAY",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-SECONDARYNAMENODE-BASE",
        "displayName" : "SecondaryNameNode Default Group",
        "roleType" : "SECONDARYNAMENODE",
        "base" : true,
        "serviceRef" : {
          "clusterName" : "cluster",
          "serviceName" : "hdfs"
        },
        "config" : {
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn",
            "sensitive" : false
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "659554304",
            "sensitive" : false
          } ]
        }
      } ],
      "replicationSchedules" : [ {
        "id" : 4,
        "startTime" : "2017-06-20T18:08:07.652Z",
        "interval" : 0,
        "intervalUnit" : "MINUTE",
        "paused" : false,
        "nextRun" : null,
        "alertOnStart" : false,
        "alertOnSuccess" : false,
        "alertOnFail" : false,
        "alertOnAbort" : false,
        "hdfsArguments" : {
          "sourceService" : {
            "peerName" : "dfadeyev",
            "clusterName" : "cluster",
            "serviceName" : "hdfs"
          },
          "sourcePath" : "/user/dfadeyev/dfadeyev/part-m-00000",
          "destinationPath" : "/labs/storage/dest",
          "mapreduceServiceName" : "yarn",
          "dryRun" : false,
          "abortOnError" : false,
          "removeMissingFiles" : false,
          "preserveReplicationCount" : true,
          "preserveBlockSize" : true,
          "preservePermissions" : true,
          "skipChecksumChecks" : false,
          "skipTrash" : false,
          "replicationStrategy" : "DYNAMIC",
          "preserveXAttrs" : false,
          "exclusionFilters" : [ ]
        },
        "active" : false
      } ],
      "snapshotPolicies" : [ ]
    } ],
    "parcels" : [ {
      "product" : "CDH",
      "version" : "5.9.1-1.cdh5.9.1.p0.4",
      "stage" : "DISTRIBUTED",
      "clusterRef" : {
        "clusterName" : "cluster"
      }
    }, {
      "product" : "CDH",
      "version" : "5.9.1-1.cdh5.9.1.p0.4",
      "stage" : "ACTIVATED",
      "clusterRef" : {
        "clusterName" : "cluster"
      }
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe",
    "ipAddress" : "172.28.210.128",
    "hostname" : "feng-xu-1.vpc.cloudera.com",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "e61a2a7d-a4f2-4f3a-8105-f25e2c044607",
    "ipAddress" : "172.28.211.85",
    "hostname" : "feng-xu-2.vpc.cloudera.com",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "9e6be5c9-ee1c-4843-9b51-442dff82fb50",
    "ipAddress" : "172.28.193.196",
    "hostname" : "feng-xu-3.vpc.cloudera.com",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "2466595c-00c7-41ec-9981-e0dc2896596a",
    "ipAddress" : "172.28.198.163",
    "hostname" : "feng-xu-4.vpc.cloudera.com",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "87bd4519-f38e-466e-ac61-bdf13b693137",
    "ipAddress" : "172.28.197.155",
    "hostname" : "feng-xu-5.vpc.cloudera.com",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__b93b4c65-bd56-455c-a5a3-83d65ea9b30c",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "1293cfb6e15157b6e0f2c8c4d7db0b900b7fe7cf7c297edf16b2af06e2e58927",
    "pwSalt" : 7263598145057965782,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-b3816d202d81ada101b80d98fea158bb",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "38b6bf46463a7c1288579d93e516873c87a3aeb55eea7cb5a7cd1995568b3b82",
    "pwSalt" : -1061169995340554740,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-b3816d202d81ada101b80d98fea158bb",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "44dd3afc197ad011b3e5549f82b64adacff3cc075c9b7a5c1014874258f361d0",
    "pwSalt" : -941719294962114524,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-b3816d202d81ada101b80d98fea158bb",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "3f2c570b7b51e4b725fa1d6f2b1641b1218d549eb59542ff811e4ea63c3bf3f5",
    "pwSalt" : -3932438181340871101,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-b3816d202d81ada101b80d98fea158bb",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "9247d9b5c4c679d2bed6f679af864fdf3f5585327672ce733f62e61d377d15f8",
    "pwSalt" : 3442462170650513500,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "032457069a9e3cbbbc1da3eeca928aa31fab067c90345a9b2fd7303dfcded5d2",
    "pwSalt" : -3151544592519777648,
    "pwLogin" : true
  }, {
    "name" : "fx185000",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "e6daacf53b4f1d87229dd2e61913f5136b979ff6241d4bbb47849d122a404cc4",
    "pwSalt" : 5618256503379710074,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "e118769a452fb45c72a5ee73bbc1c2c39dd86822548b1de02af68b85972770dc",
    "pwSalt" : -2587612861913264008,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.9.1",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20170112-1158",
    "gitHash" : "a66d8bbdbe8bc3ee54235e55423f2f76c7d9f3b1",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-b3816d202d81ada101b80d98fea158bb",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "2q30n3zobcymzfqtp47co9qx1",
          "sensitive" : true
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-ALERTPUBLISHER-BASE"
      }
    }, {
      "name" : "mgmt-EVENTSERVER-b3816d202d81ada101b80d98fea158bb",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "7vz4xvicf3iw5dcpb6wn2v298",
          "sensitive" : true
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-EVENTSERVER-BASE"
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-b3816d202d81ada101b80d98fea158bb",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "cwwkx3yux8vi6ae5lu95ezvih",
          "sensitive" : true
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-HOSTMONITOR-BASE"
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-b3816d202d81ada101b80d98fea158bb",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "93anjxw8p2dloh5kc7gxth94r",
          "sensitive" : true
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-REPORTSMANAGER-BASE"
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-b3816d202d81ada101b80d98fea158bb",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "67da7d10-acb6-466c-95a6-fc174a2ecffe"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "b1h7m6rd7zqxeezd2mkvyrvzl",
          "sensitive" : true
        } ]
      },
      "roleConfigGroupRef" : {
        "roleConfigGroupName" : "mgmt-SERVICEMONITOR-BASE"
      }
    } ],
    "displayName" : "Cloudera Management Service",
    "roleConfigGroups" : [ {
      "name" : "mgmt-ACTIVITYMONITOR-BASE",
      "displayName" : "Activity Monitor Default Group",
      "roleType" : "ACTIVITYMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-ALERTPUBLISHER-BASE",
      "displayName" : "Alert Publisher Default Group",
      "roleType" : "ALERTPUBLISHER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-BASE",
      "displayName" : "Event Server Default Group",
      "roleType" : "EVENTSERVER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "659554304",
          "sensitive" : false
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-BASE",
      "displayName" : "Host Monitor Default Group",
      "roleType" : "HOSTMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "659554304",
          "sensitive" : false
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "857735168",
          "sensitive" : false
        } ]
      }
    }, {
      "name" : "mgmt-NAVIGATOR-BASE",
      "displayName" : "Navigator Audit Server Default Group",
      "roleType" : "NAVIGATOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-NAVIGATORMETASERVER-BASE",
      "displayName" : "Navigator Metadata Server Default Group",
      "roleType" : "NAVIGATORMETASERVER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-BASE",
      "displayName" : "Reports Manager Default Group",
      "roleType" : "REPORTSMANAGER",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "feng-xu-1.vpc.cloudera.com",
          "sensitive" : false
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman",
          "sensitive" : false
        }, {
          "name" : "headlamp_database_password",
          "value" : "Root123~",
          "sensitive" : true
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman",
          "sensitive" : false
        }, {
          "name" : "headlamp_heapsize",
          "value" : "659554304",
          "sensitive" : false
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-BASE",
      "displayName" : "Service Monitor Default Group",
      "roleType" : "SERVICEMONITOR",
      "base" : true,
      "serviceRef" : {
        "serviceName" : "mgmt"
      },
      "config" : {
        "items" : [ {
          "name" : "firehose_heapsize",
          "value" : "659554304",
          "sensitive" : false
        }, {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "857735168",
          "sensitive" : false
        } ]
      }
    } ]
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/24/2012 1:50",
      "sensitive" : false
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "NOT_ON_PUBLIC_CLOUD",
      "sensitive" : false
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "http://172.28.210.128/parcel/",
      "sensitive" : false
    } ]
  },
  "allHostsConfig" : {
    "items" : [ {
      "name" : "rm_enabled",
      "value" : "true",
      "sensitive" : false
    } ]
  },
  "peers" : [ {
    "name" : "dfadeyev",
    "type" : "REPLICATION",
    "url" : "http://dfadeyev-1.gce.cloudera.com:7180",
    "username" : "__cloudera_internal_user__fef23699-e028-472c-afe7-80bc46fa7c67",
    "password" : "e8745243-1d81-4b39-bcfd-70756c9ef186e154f825-cb3c-4ddc-8a0b-8aeeb62f294d",
    "clouderaManagerCreatedUser" : true
  } ],
  "hostTemplates" : {
    "items" : [ ]
  }
}
```