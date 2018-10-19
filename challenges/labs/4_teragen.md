Teragen command

	sudo -u raffles time hadoop jar /opt/cloudera/parcels/CDH-5.14.4-1.cdh5.14.4.p0.3/jars/hadoop-mapreduce-examples-2.6.0-cdh5.14.4.jar teragen -Dmapreduce.job.maps=6 -Ddfs.block.size=33554432 51200000 /user/raffles/tgen512


Time output

	real    5m6.546s
	user    0m3.225s
	sys     2m2.554s


Command and output

	[daniramirez@sebc-vm1-challenges ~]$ sudo -u hdfs hdfs dfs -ls /user/raffles/tgen512
	Found 7 items
	-rw-r--r--   3 raffles raffles          0 2018-10-19 08:59 /user/raffles/tgen512/_SUCCESS
	-rw-r--r--   3 raffles raffles  853333400 2018-10-19 08:59 /user/raffles/tgen512/part-m-00000
	-rw-r--r--   3 raffles raffles  853333300 2018-10-19 08:59 /user/raffles/tgen512/part-m-00001
	-rw-r--r--   3 raffles raffles  853333300 2018-10-19 08:59 /user/raffles/tgen512/part-m-00002
	-rw-r--r--   3 raffles raffles  853333400 2018-10-19 08:59 /user/raffles/tgen512/part-m-00003
	-rw-r--r--   3 raffles raffles  853333300 2018-10-19 08:59 /user/raffles/tgen512/part-m-00004
	-rw-r--r--   3 raffles raffles  853333300 2018-10-19 08:59 /user/raffles/tgen512/part-m-00005


Blocks associated with this directory

	[daniramirez@sebc-vm1-challenges ~]$ sudo -u hdfs hdfs fsck -blocks /user/raffles
	Connecting to namenode via http://sebc-vm1-challenge.francecentral.cloudapp.azure.com:50070/fsck?ugi=hdfs&blocks=1&path=%2Fuser%2Fraffles
	FSCK started by hdfs (auth:SIMPLE) from /10.0.3.4 for path /user/raffles at Fri Oct 19 09:02:15 UTC 2018
	.......Status: HEALTHY
	 Total size:    5120000000 B
	 Total dirs:    3
	 Total files:   7
	 Total symlinks:                0
	 Total blocks (validated):      156 (avg. block size 32820512 B)
	 Minimally replicated blocks:   156 (100.0 %)
	 Over-replicated blocks:        0 (0.0 %)
	 Under-replicated blocks:       0 (0.0 %)
	 Mis-replicated blocks:         0 (0.0 %)
	 Default replication factor:    3
	 Average block replication:     3.0
	 Corrupt blocks:                0
	 Missing replicas:              0 (0.0 %)
	 Number of data-nodes:          4
	 Number of racks:               1
	FSCK ended at Fri Oct 19 09:02:15 UTC 2018 in 9 milliseconds


	The filesystem under path '/user/raffles' is HEALTHY
