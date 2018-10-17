```
{
  "timestamp" : "2018-10-17T10:08:57.192Z",
  "clusters" : [ {
    "name" : "tizemrane",
    "version" : "CDH5",
    "services" : [ {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-1a0a914e08519f9f707f9e84e866ff26",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "2b7f13a1-a92a-4e87-8f7d-91247ac6902e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "5511xskmbjlae7aeqx978ae5z"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "frdywhns4bddxruyv6n7ama6"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9n65wrc97mf5zx5zh39f0i4ah"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "n1.sebcdomain"
          }, {
            "name" : "oozie_database_password",
            "value" : "password"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozieuser"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-4e86cecf99cc970995356bd5152d536a",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2ycaczerkz6e411nylxdnxgwn"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "n1.sebcdomain"
        }, {
          "name" : "database_password",
          "value" : "password"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "database_user",
          "value" : "hueuser"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-4e86cecf99cc970995356bd5152d536a"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-4e86cecf99cc970995356bd5152d536a",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
        },
        "config" : {
          "items" : [ {
            "name" : "navmetadataserver_cmdb_password",
            "value" : "cb00e1ff-3efa-4816-8644-c07a8fed4c5a"
          }, {
            "name" : "role_jceks_password",
            "value" : "81n96u3x6r0sv91iy4vc6m6ls"
          }, {
            "name" : "secret_key",
            "value" : "xuhW9IqFlED58inJZqTuLp2zXkLGUg"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "10555276902"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          }, {
            "name" : "namenode_java_heapsize",
            "value" : "1254096896"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          }, {
            "name" : "secondary_namenode_java_heapsize",
            "value" : "1254096896"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "LyIxK5c6D4sRwPoMd14Vsq4oZljIsT"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "eh3Z2qY28DYAieZs4sohY5zdS27M0I"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "wUtkWAxN2zESK6WisQwZvQJjGHsolK"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "10"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-0eb91b31843ef7824b09e028812f4b0b",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "119a35ba-e48c-4cee-9c92-f3afd1f6f869"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ah7s12p18nadluvxlue6xdquw"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-1a0a914e08519f9f707f9e84e866ff26",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "2b7f13a1-a92a-4e87-8f7d-91247ac6902e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ewul1gzf47d26gpav2hfwg59w"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1o0mfdj9mghcsh35hs63311dh"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9koyhqef26tu5d73lsx3sla6y"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "197clf303qvju8kd847c6xk6r"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ex69foqq5ae7zb25tweww3aem"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-4e86cecf99cc970995356bd5152d536a",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "ajjb0gsgcuhfktkfxdm4d3ynu"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-0eb91b31843ef7824b09e028812f4b0b",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "119a35ba-e48c-4cee-9c92-f3afd1f6f869"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "chmpfz5bdcm046q6szq2t0v3"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-1a0a914e08519f9f707f9e84e866ff26",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "2b7f13a1-a92a-4e87-8f7d-91247ac6902e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "dx6k3sy4n72f4gkxbo6h6ywi"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-4e86cecf99cc970995356bd5152d536a",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "a549k5jh3k7g0k8jphaib57dd"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "sebc"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "sebc"
          }, {
            "name" : "namenode_id",
            "value" : "42"
          }, {
            "name" : "role_jceks_password",
            "value" : "8u6bomnq14m7z2snzia3h4s02"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "sebc"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "sebc"
          }, {
            "name" : "namenode_id",
            "value" : "53"
          }, {
            "name" : "role_jceks_password",
            "value" : "9pp2v76mjhkias86x0x7edjbj"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "8"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "3"
          }, {
            "name" : "mapreduce_job_ubertask_enabled",
            "value" : "true"
          }, {
            "name" : "mapreduce_job_ubertask_maxbytes",
            "value" : "536870912"
          }, {
            "name" : "mapreduce_job_ubertask_maxmaps",
            "value" : "5"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "4"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "6144"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "yarn_scheduler_increment_allocation_mb",
            "value" : "1024"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4346"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "true"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "90"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "VjXrgE18WTRLUYT0zpiVAqZryqkgnL"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "54qj5ukvdbje6i6ki633t7dn"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-0eb91b31843ef7824b09e028812f4b0b",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "119a35ba-e48c-4cee-9c92-f3afd1f6f869"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "blgabj8bjnoylo9pom1irg4kc"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-1a0a914e08519f9f707f9e84e866ff26",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "2b7f13a1-a92a-4e87-8f7d-91247ac6902e"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "alytyg1qdnno5gf3chrcf3khz"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2a9ekwpccqypxs6mzxvjspp35"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-e7237677cf4a51aa33b33c4f1fc001f6",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "d5835167-843b-46ad-8570-df955aebfd15"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "eizakizy25bk5847knxx7o9pk"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-1a0a914e08519f9f707f9e84e866ff26",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "2b7f13a1-a92a-4e87-8f7d-91247ac6902e"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "49"
          }, {
            "name" : "role_jceks_password",
            "value" : "aezcgzuwiqucfvlmen5q6y8km"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "1254096896"
          }, {
            "name" : "hive_metastore_server_max_message_size",
            "value" : "125409689"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "1254096896"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "1385955328"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "233"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "n1.sebcdomain"
        }, {
          "name" : "hive_metastore_database_name",
          "value" : "hive"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "password"
        }, {
          "name" : "hive_metastore_database_user",
          "value" : "hiveuser"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-4e86cecf99cc970995356bd5152d536a",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bl3fhzonhv01hm4r84swm7dyn"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-9763d2a3b008fe36d1ac87e36a78598c",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7mqhmtaovygkr3d0idkphc220"
          } ]
        }
      } ],
      "displayName" : "Hive"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712",
    "ipAddress" : "172.31.24.141",
    "hostname" : "n1.sebcdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "8a083683-6a48-4d86-ab2b-061aca7f27aa",
    "ipAddress" : "172.31.19.154",
    "hostname" : "n2.sebcdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "d5835167-843b-46ad-8570-df955aebfd15",
    "ipAddress" : "172.31.24.226",
    "hostname" : "n3.sebcdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "2b7f13a1-a92a-4e87-8f7d-91247ac6902e",
    "ipAddress" : "172.31.26.160",
    "hostname" : "n4.sebcdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "119a35ba-e48c-4cee-9c92-f3afd1f6f869",
    "ipAddress" : "172.31.29.200",
    "hostname" : "n5.sebcdomain",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__57946ba3-9d4c-418f-8e9c-2c3f7bd03d17",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "59a38d4837bb4d8155ce5843502d1265d6913b7781276e0a443e307f06ea8101",
    "pwSalt" : 5749314255741156572,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__hue-HUE_SERVER-4e86cecf99cc970995356bd5152d536a",
    "roles" : [ "ROLE_NAVIGATOR_ADMIN" ],
    "pwHash" : "32c107a32fc67d17546205ba82a9bedb90eab573855049eb3b1b9b7059b06722",
    "pwSalt" : 1866494507562898680,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-4e86cecf99cc970995356bd5152d536a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "149688b89a7462340b9c5cb5158839cab08481d0998e58d6230033c47fa90dae",
    "pwSalt" : -8599405079144032182,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-4e86cecf99cc970995356bd5152d536a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "e7bc42d8349c62d2b33f736fa4d60d0fe9d068dc72326213ea0ddcd5e3a37181",
    "pwSalt" : 2160297038322805493,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-4e86cecf99cc970995356bd5152d536a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "dcd53aaa222c208ae148b86f32b34129538b9d38cbb10d7528b2e2505fad48ad",
    "pwSalt" : -7997919004783290444,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-4e86cecf99cc970995356bd5152d536a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "6a56bacf480bd4a5114c40fa258afe448c865084d83b86c43794e7b7d5777253",
    "pwSalt" : -6844978488861857348,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "671ee34e7df3a156e3f7bef42e1b43d9a6b5973e3e07e20b43b1036b883c73ec",
    "pwSalt" : -6338469530036390759,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "54ef388875cca3c412b0f22f56716dd88a19217c5a6de880382d94daac253347",
    "pwSalt" : -8390468653371200079,
    "pwLogin" : true
  }, {
    "name" : "tizemrane",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "9256f829fe29e9cd4ac5f89a9985909c53837adc5198cf2b841f312db184b2fe",
    "pwSalt" : -6174158328945538767,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.13.3",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20180328-1830",
    "gitHash" : "f90c58536c252d70a23bde6d94514d92a1f111d4",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "n1.sebcdomain"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "password"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rmanuser"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-4e86cecf99cc970995356bd5152d536a",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "e3x2tgmkxou7m5cho028v8z45"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-4e86cecf99cc970995356bd5152d536a",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "4j9bd8alrmrw56hgdrcifyubt"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-4e86cecf99cc970995356bd5152d536a",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "bicqle2bztajv2woaeg2kpis3"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-4e86cecf99cc970995356bd5152d536a",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "3oqkfrza6c9em8tegpz1h6m42"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-4e86cecf99cc970995356bd5152d536a",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "f3d9a774-815c-44a0-b4ff-acf657d71712"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "6yj00dhxuftjvetdx3uqffzdj"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/21/2012 10:00"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,http://archive.cloudera.com/kudu/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```