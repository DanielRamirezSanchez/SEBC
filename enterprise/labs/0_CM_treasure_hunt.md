What is ubertask optimization?

	If we enable this feature, Cloudera Manager tells us that "sufficently small" jobs will run in the same single Java Virtual Machine. What we obtain form this feature, is that every single job doesn't have to communicate with a Resource Manager to allocate new mappers and reducers for the new job (if it is a small job). It is going to use the same space that the previous "small job" was using, thus, avoiding the overhead associated with the launching of new containers.

	A small job is definded by the settings:
		- mapreduce.job.ubertask.maxmaps
		- mapreduce.job.ubertask.maxreduces
		- mapreduce.job.ubertask.maxbytes

Where in CM is the Kerberos Security Realm value displayed?

	If we search for "Kerberos Security Realm" in the Cloudera Manager search bar, the line we find that fits the name is "config	Settings: Kerberos Security Realm".

	Wich means this variable belongs to the general configuration of Cloudera Manager. In the Cloudera Manager settings.

	If we navigate to Cloudera Manager -> Administration -> Settings. We will find there the "Kerberos Security Realm" (default_realm) attribute, which is the same that we found through the search bar.

Which CDH service(s) host a property for enabling Kerberos authentication?

	If we use the Cloudera Manager search bar and write "Kerberos", we will be listed with all the services that have a property related with Kerberos, thus, allowing us to know which services could use Kerberos authentication. The list of services/properties is:

	- Hive: Kerberos Principal
	- Zookeeper: Kerberos Principal
	- Hue: Kerberos Principal
	- Oozie: Kerberos Principal
	- HDFS: Kerberos Principal
	- YARN (MR2 included): Kerberos Principal
	- Cloudera Management Service: Role-Specific Kerberos Principal
	- YARN (MR2 included): Role-Specific Kerberos Principal
	- HDFS: Role-Specific Kerberos Principal
	- Cloudera Management Service: Activiy Monitor Kerberos Principal
	- Cloudera Management Service: Reports Manager Kerberos Principal
	- Cloudera Management Service: Navigator Kerberos Principal
	- Cloudera Management Service: 
	- Zookeeper: Enable Kerberos Authentication

How do you upgrade the CM agents?

	We have to upgrade the packages of the agents in the Cloudera Manager server host. Then, we start the server and log into Cloudera Manager.

	We should get a page displaying the upgrade we have done and asking us if we want to do to the upgrade to all the agents in the cluster. So, using the Cloudera Manager and following the wizard, we can upgrade only once the pacakge (in the CM server host) and then distribute it through the cluster, upgrading all the related CM Agents.

Give the tsquery statement used to chart Hue's CPU utilization?

	This can be found through Cloudera Manager if we navigate to HUE -> Charts Library and look for the chart called "CPU Cores Used", if we ask to open the chart in "Chart Builder" we will see the query statement used (and be able to modify it, if needed). The query used is:

	select cpu_system_rate + cpu_user_rate where category=ROLE and serviceName=$SERVICENAME

	The variables are defined withing the context of the query. In this context, the values of the variable $SERVICENAME is 'HUE'

Name all the roles that make up the Hive service

	If we go to Cloudera Manager -> Hive -> Instances we will see the the Role Instances that are part of the Hive service in our cluster. In our case:

	- HiveServer2
	- Hive Metastore Server
	- Gateway

	But these are not all the roles that make up the Hive service, because whe don't have them all in our cluster. We can click, for instance, to 'Add Role Instances' and we will see the 3 instances that we have deployed in our cluster plus the 'WebHCat Server', wich is not present in our cluster, but still is a part of the Hive service.

	So the list of roles is:
	- HiveServer2
	- Hive Metastore Server
	- Gateway
	- WebHCat Server

What steps must be completed before integrating Cloudera Manager with Kerberos?

	Cloudera Manager provides us with a wizard we can follow to set up the integration with Kerberos. But before we can do that we have to do the following:
	- Set up a working Key Distribution Center (KDC), because CM supports integration with MIT KDC.
	- Configure the KDC to allow renewable tickets with non-zero ticket lifetime.
	- Install the OS-scpecific packages for our cluster. In my case, CentOS 7.4, we need 'openldap-clients' in the Cloudera Manager server host and 'krb5-workstation'+'krb5-libs' on all hosts.
	- Create an account for Cloudera with the proper permissions to be able to create other accounts in the KDC.