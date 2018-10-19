List repositories

	[daniramirez@sebc-vm2-challenges ~]$ ls /etc/yum.repos.d
	CentOS-Base.repo  CentOS-CR.repo  CentOS-Debuginfo.repo  CentOS-fasttrack.repo  CentOS-Media.repo  CentOS-Sources.repo  CentOS-Vault.repo  cloudera-manager.repo

Configure Database

	[daniramirez@sebc-vm2-challenges ~]$ sudo /usr/share/cmf/schema/scm_prepare_database.sh -h sebc-vm1-challenge.francecentral.cloudapp.azure.com  mysql scm scm scm
	JAVA_HOME=/usr/java/default
	Verifying that we can write to /etc/cloudera-scm-server
	Creating SCM configuration file in /etc/cloudera-scm-server
	Executing:  /usr/java/default/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
	[                          main] DbCommandExecutor              INFO  Successfully connected to database.
	All done, your SCM database is configured correctly!
