Testing that my user has no acces to tables in Hive after configuring Sentry

Authenticate my user as a Kerberos principal

	[daniramirez@sebc-vm2 ~]$ kinit danielramirezsanchez
	Password for danielramirezsanchez@HADOOP.COM: ********

Check

	[daniramirez@sebc-vm2 ~]$ klist
	Ticket cache: FILE:/tmp/krb5cc_1000
	Default principal: danielramirezsanchez@HADOOP.COM

	Valid starting       Expires              Service principal
	10/18/2018 07:52:24  10/18/2018 17:52:24  krbtgt/HADOOP.COM@HADOOP.COM
	        renew until 10/25/2018 07:52:21

Using beeline to confirm that my principal sees no tables

	[daniramirez@sebc-vm2 ~]$ beeline
	Beeline version 1.1.0-cdh5.13.3 by Apache Hive
	beeline> !connect jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	Connecting to jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
	Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
	Transaction isolation: TRANSACTION_REPEATABLE_READ
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> show tables;
	INFO  : Compiling command(queryId=hive_20181018075555_46bc9c30-66f5-4c5a-8dea-431ca576a1dd): show tables
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018075555_46bc9c30-66f5-4c5a-8dea-431ca576a1dd); Time taken: 0.819 seconds
	INFO  : Executing command(queryId=hive_20181018075555_46bc9c30-66f5-4c5a-8dea-431ca576a1dd): show tables
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018075555_46bc9c30-66f5-4c5a-8dea-431ca576a1dd); Time taken: 150.52 seconds
	INFO  : OK
	+-----------+--+
	| tab_name  |
	+-----------+--+
	+-----------+--+
	No rows selected (151.702 seconds)

Creating Sentry role with full authorization:

	[daniramirez@sebc-vm2 ~]$ klist
	Ticket cache: KEYRING:persistent:1000:krb_ccache_C62TuDE
	Default principal: danielramirezsanchez@HADOOP.COM

	Valid starting       Expires              Service principal
	10/18/2018 11:16:53  10/18/2018 21:16:53  krbtgt/HADOOP.COM@HADOOP.COM
	        renew until 10/25/2018 11:16:50

	[daniramirez@sebc-vm2 ~]$ beeline
	Beeline version 1.1.0-cdh5.13.3 by Apache Hive
	beeline> !connect jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	scan complete in 2ms
	Connecting to jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
	Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
	Transaction isolation: TRANSACTION_REPEATABLE_READ
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.>
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.>
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> create role sentry_admin;
	INFO  : Compiling command(queryId=hive_20181018112727_a941e456-9945-4502-ac56-67725e9cb5d2): create role sentry_admin
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018112727_a941e456-9945-4502-ac56-67725e9cb5d2); Time taken: 0.537 seconds
	INFO  : Executing command(queryId=hive_20181018112727_a941e456-9945-4502-ac56-67725e9cb5d2): create role sentry_admin
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018112727_a941e456-9945-4502-ac56-67725e9cb5d2); Time taken: 0.226 seconds
	INFO  : OK
	No rows affected (1.063 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
	INFO  : Compiling command(queryId=hive_20181018112727_72c36bc2-ecc8-4049-95b0-60c8d6274bcc): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018112727_72c36bc2-ecc8-4049-95b0-60c8d6274bcc); Time taken: 0.114 seconds
	INFO  : Executing command(queryId=hive_20181018112727_72c36bc2-ecc8-4049-95b0-60c8d6274bcc): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018112727_72c36bc2-ecc8-4049-95b0-60c8d6274bcc); Time taken: 0.105 seconds
	INFO  : OK
	No rows affected (0.236 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> GRANT ROLE sentry_admin TO GROUP danielramirezsanchez;
	INFO  : Compiling command(queryId=hive_20181018112828_a3f6accd-2e1c-4006-9fa7-9f8c8361e2cf): GRANT ROLE sentry_admin TO GROUP danielramirezsanchez
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018112828_a3f6accd-2e1c-4006-9fa7-9f8c8361e2cf); Time taken: 0.076 seconds
	INFO  : Executing command(queryId=hive_20181018112828_a3f6accd-2e1c-4006-9fa7-9f8c8361e2cf): GRANT ROLE sentry_admin TO GROUP danielramirezsanchez
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018112828_a3f6accd-2e1c-4006-9fa7-9f8c8361e2cf); Time taken: 0.09 seconds
	INFO  : OK
	No rows affected (0.182 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> show tables;
	INFO  : Compiling command(queryId=hive_20181018112828_62ed23ee-97fd-44e0-809e-470e2f731679): show tables
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018112828_62ed23ee-97fd-44e0-809e-470e2f731679); Time taken: 0.295 seconds
	INFO  : Executing command(queryId=hive_20181018112828_62ed23ee-97fd-44e0-809e-470e2f731679): show tables
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018112828_62ed23ee-97fd-44e0-809e-470e2f731679); Time taken: 0.267 seconds
	INFO  : OK
	+------------+--+
	|  tab_name  |
	+------------+--+
	| employee   |
	| products   |
	| sample_07  |
	| sample_08  |
	+------------+--+
	4 rows selected (0.626 seconds)

Creating test roles and granting privilegies

	[daniramirez@sebc-vm2 ~]$ beeline
	Beeline version 1.1.0-cdh5.13.3 by Apache Hive
	beeline> !connect jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	scan complete in 3ms
	Connecting to jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
	Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
	Transaction isolation: TRANSACTION_REPEATABLE_READ
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> CREATE ROLE reads;
	INFO  : Compiling command(queryId=hive_20181018113333_bac96ca7-8ba7-484e-acba-ff1a403423f2): CREATE ROLE reads
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113333_bac96ca7-8ba7-484e-acba-ff1a403423f2); Time taken: 0.091 seconds
	INFO  : Executing command(queryId=hive_20181018113333_bac96ca7-8ba7-484e-acba-ff1a403423f2): CREATE ROLE reads
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113333_bac96ca7-8ba7-484e-acba-ff1a403423f2); Time taken: 0.03 seconds
	INFO  : OK
	No rows affected (0.208 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> CREATE ROLE writes;
	INFO  : Compiling command(queryId=hive_20181018113333_fd1c7fca-b6a8-4680-851d-8a0c5521e09d): CREATE ROLE writes
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113333_fd1c7fca-b6a8-4680-851d-8a0c5521e09d); Time taken: 0.074 seconds
	INFO  : Executing command(queryId=hive_20181018113333_fd1c7fca-b6a8-4680-851d-8a0c5521e09d): CREATE ROLE writes
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113333_fd1c7fca-b6a8-4680-851d-8a0c5521e09d); Time taken: 0.023 seconds
	INFO  : OK
	No rows affected (0.12 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> GRANT SELECT ON DATABASE default TO ROLE reads;
	INFO  : Compiling command(queryId=hive_20181018113333_e2faa732-d0af-4d0c-ad06-96ef5ea97fc4): GRANT SELECT ON DATABASE default TO ROLE reads
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113333_e2faa732-d0af-4d0c-ad06-96ef5ea97fc4); Time taken: 0.08 seconds
	INFO  : Executing command(queryId=hive_20181018113333_e2faa732-d0af-4d0c-ad06-96ef5ea97fc4): GRANT SELECT ON DATABASE default TO ROLE reads
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113333_e2faa732-d0af-4d0c-ad06-96ef5ea97fc4); Time taken: 0.028 seconds
	INFO  : OK
	No rows affected (0.123 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> GRANT ROLE reads TO GROUP selector;
	INFO  : Compiling command(queryId=hive_20181018113333_0ac90b33-d0c6-4c95-b897-75986b06730f): GRANT ROLE reads TO GROUP selector
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113333_0ac90b33-d0c6-4c95-b897-75986b06730f); Time taken: 0.073 seconds
	INFO  : Executing command(queryId=hive_20181018113333_0ac90b33-d0c6-4c95-b897-75986b06730f): GRANT ROLE reads TO GROUP selector
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113333_0ac90b33-d0c6-4c95-b897-75986b06730f); Time taken: 0.023 seconds
	INFO  : OK
	No rows affected (0.112 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> REVOKE ALL ON DATABASE default FROM ROLE writes;
	INFO  : Compiling command(queryId=hive_20181018113434_311df687-131e-4d9d-b27b-d1c7243f4215): REVOKE ALL ON DATABASE default FROM ROLE writes
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113434_311df687-131e-4d9d-b27b-d1c7243f4215); Time taken: 0.084 seconds
	INFO  : Executing command(queryId=hive_20181018113434_311df687-131e-4d9d-b27b-d1c7243f4215): REVOKE ALL ON DATABASE default FROM ROLE writes
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113434_311df687-131e-4d9d-b27b-d1c7243f4215); Time taken: 0.063 seconds
	INFO  : OK
	No rows affected (0.165 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> GRANT SELECT ON default.sample_07 TO ROLE writes;
	INFO  : Compiling command(queryId=hive_20181018113434_dd4d9f2b-bf16-4fff-818c-5eb2aec49958): GRANT SELECT ON default.sample_07 TO ROLE writes
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113434_dd4d9f2b-bf16-4fff-818c-5eb2aec49958); Time taken: 0.077 seconds
	INFO  : Executing command(queryId=hive_20181018113434_dd4d9f2b-bf16-4fff-818c-5eb2aec49958): GRANT SELECT ON default.sample_07 TO ROLE writes
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113434_dd4d9f2b-bf16-4fff-818c-5eb2aec49958); Time taken: 0.038 seconds
	INFO  : OK
	No rows affected (0.133 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> GRANT ROLE writes TO GROUP inserters;
	INFO  : Compiling command(queryId=hive_20181018113434_f83c4697-93d2-403f-941b-f331eedd4c43): GRANT ROLE writes TO GROUP inserters
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018113434_f83c4697-93d2-403f-941b-f331eedd4c43); Time taken: 0.076 seconds
	INFO  : Executing command(queryId=hive_20181018113434_f83c4697-93d2-403f-941b-f331eedd4c43): GRANT ROLE writes TO GROUP inserters
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018113434_f83c4697-93d2-403f-941b-f331eedd4c43); Time taken: 0.031 seconds
	INFO  : OK
	No rows affected (0.122 seconds)

Created roles

	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> show roles;
	INFO  : Compiling command(queryId=hive_20181018163737_aa03061f-711f-4281-a65a-419a6b0c9c8d): show roles
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:role, type:string, comment:from deserializer)], properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018163737_aa03061f-711f-4281-a65a-419a6b0c9c8d); Time taken: 0.099 seconds
	INFO  : Executing command(queryId=hive_20181018163737_aa03061f-711f-4281-a65a-419a6b0c9c8d): show roles
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018163737_aa03061f-711f-4281-a65a-419a6b0c9c8d); Time taken: 0.065 seconds
	INFO  : OK
	+---------------+--+
	|     role      |
	+---------------+--+
	| writes        |
	| reads         |
	| sentry_admin  |
	+---------------+--+
	3 rows selected (0.311 seconds)


Show tables with test users

	[daniramirez@sebc-vm2 ~]$ kinit george
	Password for george@HADOOP.COM:
	[daniramirez@sebc-vm2 ~]$ klist
	Ticket cache: KEYRING:persistent:1000:krb_ccache_zRmqpGr
	Default principal: george@HADOOP.COM

	Valid starting       Expires              Service principal
	10/18/2018 11:42:33  10/18/2018 21:42:33  krbtgt/HADOOP.COM@HADOOP.COM
	        renew until 10/25/2018 11:42:30
	[daniramirez@sebc-vm2 ~]$ beeline
	Beeline version 1.1.0-cdh5.13.3 by Apache Hive
	beeline> !connect jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	scan complete in 2ms
	Connecting to jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
	Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
	Transaction isolation: TRANSACTION_REPEATABLE_READ
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> show tables;
	INFO  : Compiling command(queryId=hive_20181018114242_1d0aecc0-0f7e-4731-b947-d1a8eed63ba5): show tables
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018114242_1d0aecc0-0f7e-4731-b947-d1a8eed63ba5); Time taken: 0.073 seconds
	INFO  : Executing command(queryId=hive_20181018114242_1d0aecc0-0f7e-4731-b947-d1a8eed63ba5): show tables
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018114242_1d0aecc0-0f7e-4731-b947-d1a8eed63ba5); Time taken: 0.199 seconds
	INFO  : OK
	+------------+--+
	|  tab_name  |
	+------------+--+
	| employee   |
	| products   |
	| sample_07  |
	| sample_08  |
	+------------+--+
	4 row selected (0.458 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> !quit
	Closing: 0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM

	[daniramirez@sebc-vm2 ~]$ kinit ferdinand
	Password for ferdinand@HADOOP.COM:
	[daniramirez@sebc-vm2 ~]$ beeline
	Beeline version 1.1.0-cdh5.13.3 by Apache Hive
	beeline> !connect jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	scan complete in 2ms
	Connecting to jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
	Connected to: Apache Hive (version 1.1.0-cdh5.13.3)
	Driver: Hive JDBC (version 1.1.0-cdh5.13.3)
	Transaction isolation: TRANSACTION_REPEATABLE_READ
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.> show tables;
	INFO  : Compiling command(queryId=hive_20181018114343_2890ec90-2524-49f7-bd93-bb4eaddd1282): show tables
	INFO  : Semantic Analysis Completed
	INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
	INFO  : Completed compiling command(queryId=hive_20181018114343_2890ec90-2524-49f7-bd93-bb4eaddd1282); Time taken: 0.079 seconds
	INFO  : Executing command(queryId=hive_20181018114343_2890ec90-2524-49f7-bd93-bb4eaddd1282): show tables
	INFO  : Starting task [Stage-0:DDL] in serial mode
	INFO  : Completed executing command(queryId=hive_20181018114343_2890ec90-2524-49f7-bd93-bb4eaddd1282); Time taken: 0.181 seconds
	INFO  : OK
	+-----------+--+
	| tab_name  |
	+-----------+--+
	| sample_07 |
	+-----------+--+
	1 row selected (0.403 seconds)
	0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.>!quit
	Closing: 0: jdbc:hive2://sebc-vm2.westeurope.cloudapp.azure.com:10000/default;principal=hive/sebc-vm2.westeurope.cloudapp.azure.com@HADOOP.COM
