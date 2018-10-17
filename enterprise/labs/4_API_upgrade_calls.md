Use the API on the command line to (password hidden in all commands):

Report the latest available version of the API :

```

[daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez:******** "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/version"
v19

```


Report the CM version:

```

[daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez:******** "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v19/cm/version"
{
  "version" : "5.14.4",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20180707-0445",
  "gitHash" : "0971e84bdceb60db9b96533f46451f40ed8cbdf9",
  "snapshot" : false
}

```


List all CM users:

```

[daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez:******** "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v19/users"
{
  "items" : [ {
    "name" : "DanielRamirezSanchez",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}

```


Report the database server in use by CM:

```

[daniramirez@sebc-vm2 ~]$ curl --user DanielRamirezSanchez:******** "http://sebc-vm1.westeurope.cloudapp.azure.com:7180/api/v19/cm/scmDbInfo"
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}

```