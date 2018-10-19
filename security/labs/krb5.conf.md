[daniramirez@SEBC-Cloudera-vm1 ~]$ sudo cat /etc/krb5.conf

	# Configuration snippets may be placed in this directory as well
	includedir /etc/krb5.conf.d/

	[logging]
	 default = FILE:/var/log/krb5libs.log
	 kdc = FILE:/var/log/krb5kdc.log
	 admin_server = FILE:/var/log/kadmind.log

	[libdefaults]
	 dns_lookup_realm = false
	 ticket_lifetime = 24h
	 renew_lifetime = 7d
	 forwardable = true
	 rdns = false
	 default_realm = HADOOP.COM
	 default_ccache_name = KEYRING:persistent:%{uid}

	[realms]
	 HADOOP.COM = {
	  kdc = sebc-vm1.westeurope.cloudapp.azure.com:88
	  admin_server = sebc-vm1.westeurope.cloudapp.azure.com:749
	 }

	[domain_realm]
	 .westeurope.cloudapp.azure.com = HADOOP.COM
	  westeurope.cloudapp.azure.com = HADOOP.COM