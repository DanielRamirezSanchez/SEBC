The kinit command you use to authenticate your test user

	[daniramirez@SEBC-Cloudera-vm1 ~]$ kinit DanielRamirezSanchez
	Password for DanielRamirezSanchez@HADOOP.COM:

The output from a klist command listing your credentials and ticket lifetime

	[daniramirez@SEBC-Cloudera-vm1 ~]$ klist
	Ticket cache: KEYRING:persistent:1000:krb_ccache_792gDWU
	Default principal: DanielRamirezSanchez@HADOOP.COM

	Valid starting       Expires              Service principal
	10/17/2018 19:08:52  10/18/2018 05:08:52  krbtgt/HADOOP.COM@HADOOP.COM
	        renew until 10/24/2018 19:08:50

