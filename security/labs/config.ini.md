Enabling TLS Level 1 Security 

Followed the instructions, changed the use_tls=0 to use_tls=1 on every Agent host, set "Use TLS Encryption for Agents" to true and so on. After restarting the cloudera-scm-server service and all the cloudera-scm-agents, Cloudera Manager was unreachable.

Tailing the log file, found:

	org.apache.avro.AvroRuntimeException: java.io.FileNotFoundException: /var/lib/cloudera-scm-server/.keystore (No such file or directory)
	        at com.cloudera.server.common.HttpConnectorServer.start(HttpConnectorServer.java:89)
	        at com.cloudera.server.cmf.Main.startAgentServer(Main.java:572)
	        at com.cloudera.server.cmf.Main.startAvro(Main.java:483)
	        at com.cloudera.server.cmf.Main.run(Main.java:620)
	        at com.cloudera.server.cmf.Main.main(Main.java:217)
	Caused by: java.io.FileNotFoundException: /var/lib/cloudera-scm-server/.keystore (No such file or directory)
	        at java.io.FileInputStream.open0(Native Method)
	        at java.io.FileInputStream.open(FileInputStream.java:195)
	        at java.io.FileInputStream.<init>(FileInputStream.java:138)
	        at org.mortbay.resource.FileResource.getInputStream(FileResource.java:275)
	        at org.mortbay.jetty.security.SslSelectChannelConnector.createSSLContext(SslSelectChannelConnector.java:639)
	        at org.mortbay.jetty.security.SslSelectChannelConnector.doStart(SslSelectChannelConnector.java:613)
	        at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
	        at org.mortbay.jetty.Server.doStart(Server.java:235)
	        at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
	        at com.cloudera.server.common.HttpConnectorServer.start(HttpConnectorServer.java:87)
	        ... 4 more

Honestly, at this point I panicked. Tried to restore everything back to normal. Restore the use_tls=0 on the agents. But how to change the property that I had set to true inside Cloudera Manager? After some digging a while, found out the way to remove that configuration (the second command did the trick):

	delete from CONFIGS where ATTR='web_tls';
	delete from CONFIGS where ATTR='agent_tls'; 

And I left this part of the lab, and started with the Kerberos part.

-----------------------------------------------------------------------------------------

For my second try, I did the following:

	sudo cp $JAVA_HOME/jre/lib/security/cacerts $JAVA_HOME/jre/lib/security/jssecacerts

	sudo $JAVA_HOME/bin/keytool -genkeypair -alias cmhost -keyalg RSA -keystore /opt/cloudera/security/jks/$(hostname -f).jks -keysize 2048 -dname "CN=$(hostname -f),OU=Security,O=ClearPeaks,L=Barcelona,ST=Barcelona,C=SP" -storepass cloudera -keypass cloudera

After that, in Cloudera Manager went to the security settings and set up:

	- "Use TLS Encryption for Agents" = true
	- "Cloudera Manager TLS/SSL Server JKS Keystore File Location" = /opt/cloudera/security/jks/sebc-vm1.westeurope.cloudapp.azure.com.jks
	- "Cloudera Manager TLS/SSL Server JKS Keystore File Password" = cloudera

Again, on every agent host /etc/cloudera-scm-agent/config.ini, use_tls=0 became use_tls=1.

Restarted the services:

	sudo service cloudera-scm-server restart
	sudo service cloudera-scm-agent restart

And after that, the TLS Level 1 worked!

Here is the config.ini of on of the agents:

	[daniramirez@sebc-vm2 jks]$ sudo cat /etc/cloudera-scm-agent/config.ini
	[General]
	# Hostname of the CM server.
	server_host=10.0.2.5

	# Port that the CM server is listening on.
	server_port=7182

	## It should not normally be necessary to modify these.
	# Port that the CM agent should listen on.
	# listening_port=9000

	# IP Address that the CM agent should listen on.
	# listening_ip=

	# Hostname that the CM agent reports as its hostname. If unset, will be
	# obtained in code through something like this:
	#
	#   python -c 'import socket; \
	#              print socket.getfqdn(), \
	#                    socket.gethostbyname(socket.getfqdn())'
	#
	# listening_hostname=

	# An alternate hostname to report as the hostname for this host in CM.
	# Useful when this agent is behind a load balancer or proxy and all
	# inbound communication must connect through that proxy.
	# reported_hostname=

	# Port that supervisord should listen on.
	# NB: This only takes effect if supervisord is restarted.
	# supervisord_port=19001

	# Log file.  The supervisord log file will be placed into
	# the same directory.  Note that if the agent is being started via the
	# init.d script, /var/log/cloudera-scm-agent/cloudera-scm-agent.out will
	# also have a small amount of output (from before logging is initialized).
	# log_file=/var/log/cloudera-scm-agent/cloudera-scm-agent.log

	# Persistent state directory.  Directory to store CM agent state that
	# persists across instances of the agent process and system reboots.
	# Particularly, the agent's UUID is stored here.
	# lib_dir=/var/lib/cloudera-scm-agent

	# Parcel directory.  Unpacked parcels will be stored in this directory.
	# Downloaded parcels will be stored in <parcel_dir>/../parcel-cache
	# parcel_dir=/opt/cloudera/parcels

	# Enable supervisord event monitoring.  Used in eager heartbeating, amongst
	# other things.
	# enable_supervisord_events=true

	# Maximum time to wait (in seconds) for all metric collectors to finish
	# collecting data.
	max_collection_wait_seconds=10.0

	# Maximum time to wait (in seconds) when connecting to a local role's
	# webserver to fetch metrics.
	metrics_url_timeout_seconds=30.0

	# Maximum time to wait (in seconds) when connecting to a local TaskTracker
	# to fetch task attempt data.
	task_metrics_timeout_seconds=5.0

	# The list of non-device (nodev) filesystem types which will be monitored.
	monitored_nodev_filesystem_types=nfs,nfs4,tmpfs

	# The list of filesystem types which are considered local for monitoring purposes.
	# These filesystems are combined with the other local filesystem types found in
	# /proc/filesystems
	local_filesystem_whitelist=ext2,ext3,ext4,xfs

	# The largest size impala profile log bundle that this agent will serve to the
	# CM server. If the CM server requests more than this amount, the bundle will
	# be limited to this size. All instances of this limit being hit are logged to
	# the agent log.
	impala_profile_bundle_max_bytes=1073741824

	# The largest size stacks log bundle that this agent will serve to the CM
	# server. If the CM server requests more than this amount, the bundle will be
	# limited to this size. All instances of this limit being hit are logged to the
	# agent log.
	stacks_log_bundle_max_bytes=1073741824

	# The size to which the uncompressed portion of a stacks log can grow before it
	# is rotated. The log will then be compressed during rotation.
	stacks_log_max_uncompressed_file_size_bytes=5242880

	# The orphan process directory staleness threshold. If a diretory is more stale
	# than this amount of seconds, CM agent will remove it.
	orphan_process_dir_staleness_threshold=5184000

	# The orphan process directory refresh interval. The CM agent will check the
	# staleness of the orphan processes config directory every this amount of
	# seconds.
	orphan_process_dir_refresh_interval=3600

	# A knob to control the agent logging level. The options are listed as follows:
	# 1) DEBUG (set the agent logging level to 'logging.DEBUG')
	# 2) INFO (set the agent logging level to 'logging.INFO')
	scm_debug=INFO

	# The DNS resolution collecion interval in seconds. A java base test program
	# will be executed with at most this frequency to collect java DNS resolution
	# metrics. The test program is only executed if the associated health test,
	# Host DNS Resolution, is enabled.
	dns_resolution_collection_interval_seconds=60

	# The maximum time to wait (in seconds) for the java test program to collect
	# java DNS resolution metrics.
	dns_resolution_collection_timeout_seconds=30

	# The directory location in which the agent-wide kerberos credential cache
	# will be created.
	# agent_wide_credential_cache_location=/var/run/cloudera-scm-agent

	[Security]
	# Use TLS and certificate validation when connecting to the CM server.
	use_tls=1

	# The maximum allowed depth of the certificate chain returned by the peer.
	# The default value of 9 matches the default specified in openssl's
	# SSL_CTX_set_verify.
	max_cert_depth=9

	# A file of CA certificates in PEM format. The file can contain several CA
	# certificates identified by
	#
	# -----BEGIN CERTIFICATE-----
	# ... (CA certificate in base64 encoding) ...
	# -----END CERTIFICATE-----
	#
	# sequences. Before, between, and after the certificates text is allowed which
	# can be used e.g. for descriptions of the certificates.
	#
	# The file is loaded once, the first time an HTTPS connection is attempted. A
	# restart of the agent is required to pick up changes to the file.
	#
	# Note that if neither verify_cert_file or verify_cert_dir is set, certificate
	# verification will not be performed.
	# verify_cert_file=

	# Directory containing CA certificates in PEM format. The files each contain one
	# CA certificate. The files are looked up by the CA subject name hash value,
	# which must hence be available. If more than one CA certificate with the same
	# name hash value exist, the extension must be different (e.g. 9d66eef0.0,
	# 9d66eef0.1 etc). The search is performed in the ordering of the extension
	# number, regardless of other properties of the certificates. Use the c_rehash
	# utility to create the necessary links.
	#
	# The certificates in the directory are only looked up when required, e.g. when
	# building the certificate chain or when actually performing the verification
	# of a peer certificate. The contents of the directory can thus be changed
	# without an agent restart.
	#
	# When looking up CA certificates, the verify_cert_file is first searched, then
	# those in the directory. Certificate matching is done based on the subject name,
	# the key identifier (if present), and the serial number as taken from the
	# certificate to be verified. If these data do not match, the next certificate
	# will be tried. If a first certificate matching the parameters is found, the
	# verification process will be performed; no other certificates for the same
	# parameters will be searched in case of failure.
	#
	# Note that if neither verify_cert_file or verify_cert_dir is set, certificate
	# verification will not be performed.
	# verify_cert_dir=

	# PEM file containing client private key.
	# client_key_file=

	# A command to run which returns the client private key password on stdout
	# client_keypw_cmd=

	# If client_keypw_cmd isn't specified, instead a text file containing
	# the client private key password can be used.
	# client_keypw_file=

	# PEM file containing client certificate.
	# client_cert_file=

	## Location of Hadoop files.  These are the CDH locations when installed by
	## packages.  Unused when CDH is installed by parcels.
	[Hadoop]
	#cdh_crunch_home=/usr/lib/crunch
	#cdh_flume_home=/usr/lib/flume-ng
	#cdh_hadoop_bin=/usr/bin/hadoop
	#cdh_hadoop_home=/usr/lib/hadoop
	#cdh_hbase_home=/usr/lib/hbase
	#cdh_hbase_indexer_home=/usr/lib/hbase-solr
	#cdh_hcat_home=/usr/lib/hive-hcatalog
	#cdh_hdfs_home=/usr/lib/hadoop-hdfs
	#cdh_hive_home=/usr/lib/hive
	#cdh_httpfs_home=/usr/lib/hadoop-httpfs
	#cdh_hue_home=/usr/share/hue
	#cdh_hue_plugins_home=/usr/lib/hadoop
	#cdh_impala_home=/usr/lib/impala
	#cdh_llama_home=/usr/lib/llama
	#cdh_mr1_home=/usr/lib/hadoop-0.20-mapreduce
	#cdh_mr2_home=/usr/lib/hadoop-mapreduce
	#cdh_oozie_home=/usr/lib/oozie
	#cdh_parquet_home=/usr/lib/parquet
	#cdh_pig_home=/usr/lib/pig
	#cdh_solr_home=/usr/lib/solr
	#cdh_spark_home=/usr/lib/spark
	#cdh_sqoop_home=/usr/lib/sqoop
	#cdh_sqoop2_home=/usr/lib/sqoop2
	#cdh_yarn_home=/usr/lib/hadoop-yarn
	#cdh_zookeeper_home=/usr/lib/zookeeper
	#hive_default_xml=/etc/hive/conf.dist/hive-default.xml
	#webhcat_default_xml=/etc/hive-webhcat/conf.dist/webhcat-default.xml
	#jsvc_home=/usr/libexec/bigtop-utils
	#tomcat_home=/usr/lib/bigtop-tomcat
	#oracle_home=/usr/share/oracle/instantclient

	## Location of Cloudera Management Services files.
	[Cloudera]
	#mgmt_home=/usr/share/cmf

	## Location of JDBC Drivers.
	[JDBC]
	#cloudera_mysql_connector_jar=/usr/share/java/mysql-connector-java.jar
	#cloudera_oracle_connector_jar=/usr/share/java/oracle-connector-java.jar
	#By default, postgres jar is found dynamically in $MGMT_HOME/lib
	#cloudera_postgresql_jdbc_jar=



