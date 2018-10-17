Curl command

```
  
  curl http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v2/cm/deployment --user DanielRamirezSanchez
  Enter host password for user 'DanielRamirezSanchez':

```

After inserting the password, we obtain this output for the cluster deployment

```

  {
    "timestamp" : "2018-10-17T10:07:22.718Z",
    "clusters" : [ {
      "name" : "DanielRamirezSanchez",
      "version" : "CDH5",
      "services" : [ {
        "name" : "hive",
        "type" : "HIVE",
        "config" : {
          "roleTypeConfigs" : [ {
            "roleType" : "HIVEMETASTORE",
            "items" : [ {
              "name" : "hive_metastore_java_heapsize",
              "value" : "643825664"
            } ]
          }, {
            "roleType" : "HIVESERVER2",
            "items" : [ {
              "name" : "hiveserver2_java_heapsize",
              "value" : "643825664"
            }, {
              "name" : "hiveserver2_spark_driver_memory",
              "value" : "966367641"
            }, {
              "name" : "hiveserver2_spark_executor_cores",
              "value" : "4"
            }, {
              "name" : "hiveserver2_spark_executor_memory",
              "value" : "4220256256"
            }, {
              "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
              "value" : "102"
            }, {
              "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
              "value" : "710"
            } ]
          } ],
          "items" : [ {
            "name" : "hive_metastore_database_host",
            "value" : "sebc-vm1.westeurope.cloudapp.azure.com"
          }, {
            "name" : "hive_metastore_database_password",
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
          "name" : "hive-GATEWAY-30e120cfa35fb588e0cadebec5701b77",
          "type" : "GATEWAY",
          "hostRef" : {
            "hostId" : "57240783-a3ae-4928-9875-4171f4f9b7e6"
          },
          "config" : {
            "items" : [ ]
          }
        }, {
          "name" : "hive-GATEWAY-78e7db79095849be2627203810fb00d3",
          "type" : "GATEWAY",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ ]
          }
        }, {
          "name" : "hive-GATEWAY-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "GATEWAY",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ ]
          }
        }, {
          "name" : "hive-GATEWAY-f414fc51f2ad26f151825bb0f843ead1",
          "type" : "GATEWAY",
          "hostRef" : {
            "hostId" : "1493ae0d-f348-428a-ada5-aa527e72f38f"
          },
          "config" : {
            "items" : [ ]
          }
        }, {
          "name" : "hive-HIVEMETASTORE-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "HIVEMETASTORE",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "88z98jo4tvnnigo8w4mn715mt"
            } ]
          }
        }, {
          "name" : "hive-HIVESERVER2-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "HIVESERVER2",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "6kjtw5xeaq7wmcj80odusnriq"
            } ]
          }
        } ],
        "displayName" : "Hive"
      }, {
        "name" : "zookeeper",
        "type" : "ZOOKEEPER",
        "config" : {
          "roleTypeConfigs" : [ {
            "roleType" : "SERVER",
            "items" : [ {
              "name" : "zookeeper_server_java_heapsize",
              "value" : "643825664"
            } ]
          } ],
          "items" : [ ]
        },
        "roles" : [ {
          "name" : "zookeeper-SERVER-78e7db79095849be2627203810fb00d3",
          "type" : "SERVER",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "4q54af9vuel2526rbzxcyyqzy"
            }, {
              "name" : "serverId",
              "value" : "3"
            } ]
          }
        }, {
          "name" : "zookeeper-SERVER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "SERVER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "2pxydj8sniokocn7ht2dun14g"
            }, {
              "name" : "serverId",
              "value" : "2"
            } ]
          }
        }, {
          "name" : "zookeeper-SERVER-f414fc51f2ad26f151825bb0f843ead1",
          "type" : "SERVER",
          "hostRef" : {
            "hostId" : "1493ae0d-f348-428a-ada5-aa527e72f38f"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "5hjwyphwtmxcsidpged97pudg"
            }, {
              "name" : "serverId",
              "value" : "1"
            } ]
          }
        } ],
        "displayName" : "ZooKeeper"
      }, {
        "name" : "hue",
        "type" : "HUE",
        "config" : {
          "roleTypeConfigs" : [ ],
          "items" : [ {
            "name" : "database_host",
            "value" : "sebc-vm1.westeurope.cloudapp.azure.com"
          }, {
            "name" : "database_password",
            "value" : "hue"
          }, {
            "name" : "database_type",
            "value" : "mysql"
          }, {
            "name" : "hive_service",
            "value" : "hive"
          }, {
            "name" : "hue_webhdfs",
            "value" : "hdfs-NAMENODE-c7d45f35c8c274e093ef14f23a3c48df"
          }, {
            "name" : "oozie_service",
            "value" : "oozie"
          }, {
            "name" : "zookeeper_service",
            "value" : "zookeeper"
          } ]
        },
        "roles" : [ {
          "name" : "hue-HUE_LOAD_BALANCER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "HUE_LOAD_BALANCER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "63tvnydlknldibu68ny67vegm"
            } ]
          }
        }, {
          "name" : "hue-HUE_SERVER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "HUE_SERVER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "navmetadataserver_cmdb_password",
              "value" : "a7716b23-9812-4f09-8d96-dce2f9311629"
            }, {
              "name" : "role_jceks_password",
              "value" : "46rvn2t0l3up89mxunyb0ltvm"
            }, {
              "name" : "secret_key",
              "value" : "uYnRwORm6J6GlWsUfSStPLL8WS5obB"
            } ]
          }
        } ],
        "displayName" : "Hue"
      }, {
        "name" : "oozie",
        "type" : "OOZIE",
        "config" : {
          "roleTypeConfigs" : [ {
            "roleType" : "OOZIE_SERVER",
            "items" : [ {
              "name" : "oozie_database_host",
              "value" : "sebc-vm1.westeurope.cloudapp.azure.com"
            }, {
              "name" : "oozie_database_password",
              "value" : "oozie"
            }, {
              "name" : "oozie_database_type",
              "value" : "mysql"
            }, {
              "name" : "oozie_database_user",
              "value" : "oozie"
            }, {
              "name" : "oozie_java_heapsize",
              "value" : "643825664"
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
          "name" : "oozie-OOZIE_SERVER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "OOZIE_SERVER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "4v1iutzwm4txdpkmbj87kuq7r"
            } ]
          }
        } ],
        "displayName" : "Oozie"
      }, {
        "name" : "yarn",
        "type" : "YARN",
        "config" : {
          "roleTypeConfigs" : [ {
            "roleType" : "GATEWAY",
            "items" : [ {
              "name" : "mapred_reduce_tasks",
              "value" : "4"
            }, {
              "name" : "mapred_submit_replication",
              "value" : "2"
            } ]
          }, {
            "roleType" : "JOBHISTORY",
            "items" : [ {
              "name" : "mr2_jobhistory_java_heapsize",
              "value" : "643825664"
            } ]
          }, {
            "roleType" : "NODEMANAGER",
            "items" : [ {
              "name" : "rm_cpu_shares",
              "value" : "1800"
            }, {
              "name" : "rm_io_weight",
              "value" : "900"
            }, {
              "name" : "yarn_nodemanager_heartbeat_interval_ms",
              "value" : "100"
            }, {
              "name" : "yarn_nodemanager_local_dirs",
              "value" : "/yarn/nm,/mnt/resource/yarn/nm"
            }, {
              "name" : "yarn_nodemanager_log_dirs",
              "value" : "/yarn/container-logs,/mnt/resource/yarn/container-logs"
            }, {
              "name" : "yarn_nodemanager_resource_cpu_vcores",
              "value" : "3"
            }, {
              "name" : "yarn_nodemanager_resource_memory_mb",
              "value" : "2938"
            } ]
          }, {
            "roleType" : "RESOURCEMANAGER",
            "items" : [ {
              "name" : "resource_manager_java_heapsize",
              "value" : "643825664"
            }, {
              "name" : "yarn_scheduler_maximum_allocation_mb",
              "value" : "4602"
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
            "value" : "false"
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
            "value" : "ilQrraKZATlrxZvcI06LP6O9oXDVYD"
          }, {
            "name" : "zookeeper_service",
            "value" : "zookeeper"
          } ]
        },
        "roles" : [ {
          "name" : "yarn-JOBHISTORY-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "JOBHISTORY",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "cqd3zbxfj9dkl5ktnahmy83f4"
            } ]
          }
        }, {
          "name" : "yarn-NODEMANAGER-30e120cfa35fb588e0cadebec5701b77",
          "type" : "NODEMANAGER",
          "hostRef" : {
            "hostId" : "57240783-a3ae-4928-9875-4171f4f9b7e6"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "4za2y7yk8x81jjxivj1zp95lk"
            } ]
          }
        }, {
          "name" : "yarn-NODEMANAGER-78e7db79095849be2627203810fb00d3",
          "type" : "NODEMANAGER",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "8ceprt694t9pat93ef22zhqjk"
            } ]
          }
        }, {
          "name" : "yarn-NODEMANAGER-f414fc51f2ad26f151825bb0f843ead1",
          "type" : "NODEMANAGER",
          "hostRef" : {
            "hostId" : "1493ae0d-f348-428a-ada5-aa527e72f38f"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "aiq8knld6zaleo9wpily3151w"
            } ]
          }
        }, {
          "name" : "yarn-RESOURCEMANAGER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "RESOURCEMANAGER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "rm_id",
              "value" : "45"
            }, {
              "name" : "role_jceks_password",
              "value" : "a12pdwysc015hu6t5uko7irzh"
            } ]
          }
        } ],
        "displayName" : "YARN (MR2 Included)"
      }, {
        "name" : "hdfs",
        "type" : "HDFS",
        "config" : {
          "roleTypeConfigs" : [ {
            "roleType" : "BALANCER",
            "items" : [ {
              "name" : "balancer_java_heapsize",
              "value" : "643825664"
            } ]
          }, {
            "roleType" : "DATANODE",
            "items" : [ {
              "name" : "datanode_java_heapsize",
              "value" : "1073741824"
            }, {
              "name" : "dfs_data_dir_list",
              "value" : "/dfs/dn,/mnt/resource/dfs/dn"
            }, {
              "name" : "dfs_datanode_du_reserved",
              "value" : "5339152793"
            }, {
              "name" : "dfs_datanode_failed_volumes_tolerated",
              "value" : "1"
            }, {
              "name" : "dfs_datanode_max_locked_memory",
              "value" : "4294967296"
            }, {
              "name" : "rm_cpu_shares",
              "value" : "200"
            }, {
              "name" : "rm_io_weight",
              "value" : "100"
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
              "value" : "/dfs/nn,/mnt/resource/dfs/nn"
            }, {
              "name" : "dfs_namenode_servicerpc_address",
              "value" : "8022"
            }, {
              "name" : "namenode_java_heapsize",
              "value" : "1073741824"
            } ]
          }, {
            "roleType" : "SECONDARYNAMENODE",
            "items" : [ {
              "name" : "fs_checkpoint_dir_list",
              "value" : "/dfs/snn"
            }, {
              "name" : "secondary_namenode_java_heapsize",
              "value" : "1073741824"
            } ]
          } ],
          "items" : [ {
            "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
            "value" : "erHX2wiCZDpcoGQZTLUAS4twYvsKDg"
          }, {
            "name" : "dfs_replication",
            "value" : "2"
          }, {
            "name" : "fc_authorization_secret_key",
            "value" : "4oBsPlFIVx8o5XU75g5qYIudSdDzaj"
          }, {
            "name" : "http_auth_signature_secret",
            "value" : "rQg6fK7hOaKFBzF7sLsHzk36p9XVA3"
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
          "name" : "hdfs-BALANCER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "BALANCER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ ]
          }
        }, {
          "name" : "hdfs-DATANODE-30e120cfa35fb588e0cadebec5701b77",
          "type" : "DATANODE",
          "hostRef" : {
            "hostId" : "57240783-a3ae-4928-9875-4171f4f9b7e6"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "2g2ujhfxo9vm8t68f1pkhowzc"
            } ]
          }
        }, {
          "name" : "hdfs-DATANODE-78e7db79095849be2627203810fb00d3",
          "type" : "DATANODE",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "b2m2h64pyvr7ac5iqjpfj2ig"
            } ]
          }
        }, {
          "name" : "hdfs-DATANODE-f414fc51f2ad26f151825bb0f843ead1",
          "type" : "DATANODE",
          "hostRef" : {
            "hostId" : "1493ae0d-f348-428a-ada5-aa527e72f38f"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "6c97oiy7jptwy5rqwjqv4j247"
            } ]
          }
        }, {
          "name" : "hdfs-FAILOVERCONTROLLER-78e7db79095849be2627203810fb00d3",
          "type" : "FAILOVERCONTROLLER",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "b6zy2y5lpt171mo3m55q8xxze"
            } ]
          }
        }, {
          "name" : "hdfs-FAILOVERCONTROLLER-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "FAILOVERCONTROLLER",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "dciqxdtqr1j2nyfjx66m84yl1"
            } ]
          }
        }, {
          "name" : "hdfs-JOURNALNODE-78e7db79095849be2627203810fb00d3",
          "type" : "JOURNALNODE",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "91svcl9sgkwwdi16fg1mdvwhv"
            } ]
          }
        }, {
          "name" : "hdfs-JOURNALNODE-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "JOURNALNODE",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "bx010aoe97vmzx7yf3asdhjq5"
            } ]
          }
        }, {
          "name" : "hdfs-JOURNALNODE-f414fc51f2ad26f151825bb0f843ead1",
          "type" : "JOURNALNODE",
          "hostRef" : {
            "hostId" : "1493ae0d-f348-428a-ada5-aa527e72f38f"
          },
          "config" : {
            "items" : [ {
              "name" : "role_jceks_password",
              "value" : "nb1mijtsxrlhs8lf8liizqa4"
            } ]
          }
        }, {
          "name" : "hdfs-NAMENODE-78e7db79095849be2627203810fb00d3",
          "type" : "NAMENODE",
          "hostRef" : {
            "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331"
          },
          "config" : {
            "items" : [ {
              "name" : "autofailover_enabled",
              "value" : "true"
            }, {
              "name" : "dfs_federation_namenode_nameservice",
              "value" : "HA-Nameservice"
            }, {
              "name" : "dfs_namenode_quorum_journal_name",
              "value" : "HA-Nameservice"
            }, {
              "name" : "namenode_id",
              "value" : "51"
            }, {
              "name" : "role_jceks_password",
              "value" : "dgklzqaohnf4n5dbsu3houtld"
            } ]
          }
        }, {
          "name" : "hdfs-NAMENODE-c7d45f35c8c274e093ef14f23a3c48df",
          "type" : "NAMENODE",
          "hostRef" : {
            "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
          },
          "config" : {
            "items" : [ {
              "name" : "autofailover_enabled",
              "value" : "true"
            }, {
              "name" : "dfs_federation_namenode_nameservice",
              "value" : "HA-Nameservice"
            }, {
              "name" : "dfs_namenode_quorum_journal_name",
              "value" : "HA-Nameservice"
            }, {
              "name" : "namenode_id",
              "value" : "47"
            }, {
              "name" : "role_jceks_password",
              "value" : "74h0x9ci0nb2c27qrbs3sygr0"
            } ]
          }
        } ],
        "displayName" : "HDFS"
      } ]
    } ],
    "hosts" : [ {
      "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1",
      "ipAddress" : "10.0.2.6",
      "hostname" : "sebc-vm2.westeurope.cloudapp.azure.com",
      "rackId" : "/default",
      "config" : {
        "items" : [ ]
      }
    }, {
      "hostId" : "91d881be-d11e-4f95-adeb-6f2da0590331",
      "ipAddress" : "10.0.2.7",
      "hostname" : "sebc-vm3.westeurope.cloudapp.azure.com",
      "rackId" : "/default",
      "config" : {
        "items" : [ ]
      }
    }, {
      "hostId" : "1493ae0d-f348-428a-ada5-aa527e72f38f",
      "ipAddress" : "10.0.2.4",
      "hostname" : "sebc-vm4.westeurope.cloudapp.azure.com",
      "rackId" : "/default",
      "config" : {
        "items" : [ ]
      }
    }, {
      "hostId" : "57240783-a3ae-4928-9875-4171f4f9b7e6",
      "ipAddress" : "10.0.2.8",
      "hostname" : "sebc-vm5.westeurope.cloudapp.azure.com",
      "rackId" : "/default",
      "config" : {
        "items" : [ ]
      }
    } ],
    "users" : [ {
      "name" : "DanielRamirezSanchez",
      "roles" : [ "ROLE_ADMIN" ],
      "pwHash" : "00fbd6d3e342767788e0a2ed450b1f143f2bfea67d42d69c753dd8fccd2703c1",
      "pwSalt" : -5303955147736275128,
      "pwLogin" : true
    }, {
      "name" : "__cloudera_internal_user__hue-HUE_SERVER-c7d45f35c8c274e093ef14f23a3c48df",
      "roles" : [ "ROLE_NAVIGATOR_ADMIN" ],
      "pwHash" : "3f9fba00d891f7a42400398cedbf7324a6dd788fe9de67d09e7f3e434601c557",
      "pwSalt" : 6405546335603267688,
      "pwLogin" : true
    }, {
      "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-c7d45f35c8c274e093ef14f23a3c48df",
      "roles" : [ "ROLE_USER" ],
      "pwHash" : "87db665a611f3577886f9825219977395cd4f51149602b4a23755254c2f24e85",
      "pwSalt" : -3192705732576729936,
      "pwLogin" : true
    }, {
      "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-c7d45f35c8c274e093ef14f23a3c48df",
      "roles" : [ "ROLE_USER" ],
      "pwHash" : "3be43de9f0941a67335acba7487fdb240291ec5ddb02b5e7f5e3880bce4cfdbb",
      "pwSalt" : -1088111285049973136,
      "pwLogin" : true
    }, {
      "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-c7d45f35c8c274e093ef14f23a3c48df",
      "roles" : [ "ROLE_USER" ],
      "pwHash" : "0f8a542bac48be03873697961846da072eb7bd865d13b54c648d87ba4398ce84",
      "pwSalt" : -2193904142308667335,
      "pwLogin" : true
    }, {
      "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-c7d45f35c8c274e093ef14f23a3c48df",
      "roles" : [ "ROLE_USER" ],
      "pwHash" : "747482c6bf4f5e9ab7ccdf8d69f43f84a8d5ebdd938a2d0d497a04de62a5b447",
      "pwSalt" : 1240884347071149942,
      "pwLogin" : true
    }, {
      "name" : "admin",
      "roles" : [ "ROLE_LIMITED" ],
      "pwHash" : "2a849773525549443a9ecaed70275b74f770dfe499ff10cde4428d00a52077bc",
      "pwSalt" : -1147406245430698072,
      "pwLogin" : true
    }, {
      "name" : "minotaur",
      "roles" : [ "ROLE_CONFIGURATOR" ],
      "pwHash" : "49d03f5cc8ecb13db452ad2ce15868780399b58d145ae5c34a4ec606ad659919",
      "pwSalt" : 6904718310158764365,
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
          "roleType" : "EVENTSERVER",
          "items" : [ {
            "name" : "event_server_heapsize",
            "value" : "643825664"
          } ]
        }, {
          "roleType" : "HOSTMONITOR",
          "items" : [ {
            "name" : "firehose_heapsize",
            "value" : "643825664"
          }, {
            "name" : "firehose_non_java_memory_bytes",
            "value" : "836763648"
          } ]
        }, {
          "roleType" : "REPORTSMANAGER",
          "items" : [ {
            "name" : "headlamp_database_host",
            "value" : "sebc-vm1.westeurope.cloudapp.azure.com"
          }, {
            "name" : "headlamp_database_name",
            "value" : "rman"
          }, {
            "name" : "headlamp_database_password",
            "value" : "rman"
          }, {
            "name" : "headlamp_database_user",
            "value" : "rman"
          }, {
            "name" : "headlamp_heapsize",
            "value" : "643825664"
          } ]
        }, {
          "roleType" : "SERVICEMONITOR",
          "items" : [ {
            "name" : "firehose_heapsize",
            "value" : "643825664"
          }, {
            "name" : "firehose_non_java_memory_bytes",
            "value" : "836763648"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "mgmt-ALERTPUBLISHER-c7d45f35c8c274e093ef14f23a3c48df",
        "type" : "ALERTPUBLISHER",
        "hostRef" : {
          "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3cqmcecjh96xr3ma6siwg6px6"
          } ]
        }
      }, {
        "name" : "mgmt-EVENTSERVER-c7d45f35c8c274e093ef14f23a3c48df",
        "type" : "EVENTSERVER",
        "hostRef" : {
          "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "95y2d12ja609h52zkh824ww97"
          } ]
        }
      }, {
        "name" : "mgmt-HOSTMONITOR-c7d45f35c8c274e093ef14f23a3c48df",
        "type" : "HOSTMONITOR",
        "hostRef" : {
          "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "7mqeidnucwz49e9pptiznbz9u"
          } ]
        }
      }, {
        "name" : "mgmt-REPORTSMANAGER-c7d45f35c8c274e093ef14f23a3c48df",
        "type" : "REPORTSMANAGER",
        "hostRef" : {
          "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "96m8yidrlatilntydgwy1wc5k"
          } ]
        }
      }, {
        "name" : "mgmt-SERVICEMONITOR-c7d45f35c8c274e093ef14f23a3c48df",
        "type" : "SERVICEMONITOR",
        "hostRef" : {
          "hostId" : "fcbcf443-de46-47a4-a7b8-8f1e82f24dc1"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "52xqs0omr02xjl3p0yfjwabf3"
          } ]
        }
      } ],
      "displayName" : "Cloudera Management Service"
    },
    "managerSettings" : {
      "items" : [ {
        "name" : "CLUSTER_STATS_START",
        "value" : "10/26/2012 1:10"
      }, {
        "name" : "PUBLIC_CLOUD_STATUS",
        "value" : "NOT_ON_PUBLIC_CLOUD"
      }, {
        "name" : "REMOTE_PARCEL_REPO_URLS",
        "value" : ""
      } ]
    }
  }

```