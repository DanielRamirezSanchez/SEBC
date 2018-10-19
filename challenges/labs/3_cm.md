User folder

	[daniramirez@sebc-vm1-challenges mysql-connector-java-5.1.47]$ sudo -u hdfs hdfs dfs -ls /user
	Found 6 items
	drwxrwx--x   - fullerton fullerton          0 2018-10-19 08:48 /user/fullerton
	drwxrwxrwx   - mapred    hadoop             0 2018-10-19 08:45 /user/history
	drwxrwxr-t   - hive      hive               0 2018-10-19 08:45 /user/hive
	drwxrwxr-x   - hue       hue                0 2018-10-19 08:46 /user/hue
	drwxrwxr-x   - oozie     oozie              0 2018-10-19 08:46 /user/oozie
	drwxrwx--x   - raffles   raffles            0 2018-10-19 08:48 /user/raffles


API output

	{
	  "items" : [ {
	    "hostId" : "8d168669-18a6-4131-9730-a89f66d00480",
	    "ipAddress" : "10.0.3.4",
	    "hostname" : "sebc-vm1-challenge.francecentral.cloudapp.azure.com",
	    "rackId" : "/default",
	    "hostUrl" : "http://sebc-vm2-challenge.francecentral.cloudapp.azure.com:7180/cmf/hostRedirect/8d168669-18a6-4131-9730-a89f66d00480",
	    "maintenanceMode" : false,
	    "maintenanceOwners" : [ ],
	    "commissionState" : "COMMISSIONED",
	    "numCores" : 4,
	    "numPhysicalCores" : 4,
	    "totalPhysMemBytes" : 16811233280
	  }, {
	    "hostId" : "d38d435a-b671-4fa1-b624-53c21cfe0e9f",
	    "ipAddress" : "10.0.3.5",
	    "hostname" : "sebc-vm2-challenge.francecentral.cloudapp.azure.com",
	    "rackId" : "/default",
	    "hostUrl" : "http://sebc-vm2-challenge.francecentral.cloudapp.azure.com:7180/cmf/hostRedirect/d38d435a-b671-4fa1-b624-53c21cfe0e9f",
	    "maintenanceMode" : false,
	    "maintenanceOwners" : [ ],
	    "commissionState" : "COMMISSIONED",
	    "numCores" : 4,
	    "numPhysicalCores" : 4,
	    "totalPhysMemBytes" : 16811233280
	  }, {
	    "hostId" : "c25fde52-7aeb-4da7-8864-fb83466cf726",
	    "ipAddress" : "10.0.3.6",
	    "hostname" : "sebc-vm3-challenge.francecentral.cloudapp.azure.com",
	    "rackId" : "/default",
	    "hostUrl" : "http://sebc-vm2-challenge.francecentral.cloudapp.azure.com:7180/cmf/hostRedirect/c25fde52-7aeb-4da7-8864-fb83466cf726",
	    "maintenanceMode" : false,
	    "maintenanceOwners" : [ ],
	    "commissionState" : "COMMISSIONED",
	    "numCores" : 4,
	    "numPhysicalCores" : 4,
	    "totalPhysMemBytes" : 16811233280
	  }, {
	    "hostId" : "8f05192f-79c5-4f59-96ce-a99c70c2bce2",
	    "ipAddress" : "10.0.3.7",
	    "hostname" : "sebc-vm4-challenge.francecentral.cloudapp.azure.com",
	    "rackId" : "/default",
	    "hostUrl" : "http://sebc-vm2-challenge.francecentral.cloudapp.azure.com:7180/cmf/hostRedirect/8f05192f-79c5-4f59-96ce-a99c70c2bce2",
	    "maintenanceMode" : false,
	    "maintenanceOwners" : [ ],
	    "commissionState" : "COMMISSIONED",
	    "numCores" : 4,
	    "numPhysicalCores" : 4,
	    "totalPhysMemBytes" : 16811233280
	  }, {
	    "hostId" : "afc811ff-83c6-45cf-9c1d-6af5520f5d6f",
	    "ipAddress" : "10.0.3.8",
	    "hostname" : "sebc-vm5-challenge.francecentral.cloudapp.azure.com",
	    "rackId" : "/default",
	    "hostUrl" : "http://sebc-vm2-challenge.francecentral.cloudapp.azure.com:7180/cmf/hostRedirect/afc811ff-83c6-45cf-9c1d-6af5520f5d6f",
	    "maintenanceMode" : false,
	    "maintenanceOwners" : [ ],
	    "commissionState" : "COMMISSIONED",
	    "numCores" : 4,
	    "numPhysicalCores" : 4,
	    "totalPhysMemBytes" : 16811233280
	  } ]
	}