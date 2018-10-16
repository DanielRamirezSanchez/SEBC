Find examples jar

	[daniramirez@sebc-vm2 lib]$ sudo find / -name hadoop-mapreduce-examples*.jar
	/opt/cloudera/parcels/CDH-5.13.3-1.cdh5.13.3.p0.2/lib/hadoop-mapreduce/hadoop-mapreduce-examples-2.6.0-cdh5.13.3.jar
	/opt/cloudera/parcels/CDH-5.13.3-1.cdh5.13.3.p0.2/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar
	/opt/cloudera/parcels/CDH-5.13.3-1.cdh5.13.3.p0.2/jars/hadoop-mapreduce-examples-2.6.0-cdh5.13.3.jar
	[daniramirez@sebc-vm2 lib]$ cd /opt/cloudera/parcels/CDH-5.13.3-1.cdh5.13.3.p0.2/lib/hadoop-mapreduce/


Create the file

	sudo -u hdfs hadoop jar hadoop-mapreduce-examples-2.6.0-cdh5.13.3.jar teragen 5000000 /DanielRamirezSanchez/terasort-input

Copy the file to my own cluster

	sudo -u hdfs hadoop distcp /DanielRamirezSanchez hdfs://168.63.30.186:8020/user/DanielRamirezSanchez

Check the result

	[daniramirez@sebc-vm2 ~]$ hdfs fsck /user/DanielRamirezSanchez -files -blocks
	Connecting to namenode via http://sebc-vm2.westeurope.cloudapp.azure.com:50070/fsck?ugi=daniramirez&files=1&blocks=1&path=%2Fuser%2FDanielRamirezSanchez
	FSCK started by daniramirez (auth:SIMPLE) from /10.0.2.6 for path /user/DanielRamirezSanchez at Tue Oct 16 10:58:23 UTC 2018
	/user/DanielRamirezSanchez <dir>
	/user/DanielRamirezSanchez/terasort-input <dir>
	/user/DanielRamirezSanchez/terasort-input/_SUCCESS 0 bytes, 0 block(s):  OK

	/user/DanielRamirezSanchez/terasort-input/part-m-00000 250000000 bytes, 2 block(s):  OK
	0. BP-1026734207-10.0.2.6-1539633733656:blk_1073744415_3591 len=134217728 Live_repl=2
	1. BP-1026734207-10.0.2.6-1539633733656:blk_1073744416_3592 len=115782272 Live_repl=2

	/user/DanielRamirezSanchez/terasort-input/part-m-00001 250000000 bytes, 2 block(s):  OK
	0. BP-1026734207-10.0.2.6-1539633733656:blk_1073744412_3588 len=134217728 Live_repl=2
	1. BP-1026734207-10.0.2.6-1539633733656:blk_1073744414_3590 len=115782272 Live_repl=2

	Status: HEALTHY
	 Total size:    500000000 B
	 Total dirs:    2
	 Total files:   3
	 Total symlinks:                0
	 Total blocks (validated):      4 (avg. block size 125000000 B)
	 Minimally replicated blocks:   4 (100.0 %)
	 Over-replicated blocks:        0 (0.0 %)
	 Under-replicated blocks:       0 (0.0 %)
	 Mis-replicated blocks:         0 (0.0 %)
	 Default replication factor:    2
	 Average block replication:     2.0
	 Corrupt blocks:                0
	 Missing replicas:              0 (0.0 %)
	 Number of data-nodes:          2
	 Number of racks:               1
	FSCK ended at Tue Oct 16 10:58:23 UTC 2018 in 2 milliseconds


	The filesystem under path '/user/DanielRamirezSanchez' is HEALTHY
