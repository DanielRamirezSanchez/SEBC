Stopping the Hive service:

Command

```

  [daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez -X POST "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v12/clusters/DanielRamirezSanchez/services/hive/commands/stop"
  Enter host password for user 'DanielRamirezSanchez':

```

Response

```

  {
    "id" : 646,
    "name" : "Stop",
    "startTime" : "2018-10-17T10:50:29.025Z",
    "active" : true,
    "serviceRef" : {
      "clusterName" : "cluster",
      "serviceName" : "hive"
    }
  }

```


Starting the Hive service:

Command

```

  [daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez -X POST "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v12/clusters/DanielRamirezSanchez/services/hive/commands/start"
  Enter host password for user 'DanielRamirezSanchez':

```

Response

```

  {
    "id" : 650,
    "name" : "Start",
    "startTime" : "2018-10-17T10:52:05.785Z",
    "active" : true,
    "serviceRef" : {
      "clusterName" : "cluster",
      "serviceName" : "hive"
    }
  }

```


Obtain status of the Hive service:

Command

```

  [daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez -X GET "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v12/clusters/DanielRamirezSanchez/services/hive"
  Enter host password for user 'DanielRamirezSanchez':

```

Result

```

  {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/cmf/serviceRedirect/hive",
    "roleInstancesUrl" : "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/cmf/serviceRedirect/hive/instances",
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