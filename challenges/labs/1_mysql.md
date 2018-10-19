Hostname of DATABASE node

	sebc-vm1-challenge.francecentral.cloudapp.azure.com

DB Version

	MariaDB [(none)]> select VERSION();
	+----------------+
	| VERSION()      |
	+----------------+
	| 5.5.60-MariaDB |
	+----------------+
	1 row in set (0.00 sec)

	MariaDB [(none)]>

Database list

	MariaDB [(none)]> show databases;
	+--------------------+
	| Database           |
	+--------------------+
	| information_schema |
	| hive               |
	| hue                |
	| mysql              |
	| oozie              |
	| performance_schema |
	| rman               |
	| scm                |
	| sentry             |
	+--------------------+
	9 rows in set (0.00 sec)

	MariaDB [(none)]>
