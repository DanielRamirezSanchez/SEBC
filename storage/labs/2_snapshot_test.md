Downloading the file 

	[daniramirez@sebc-vm2 ~]$ cd /tmp
	[daniramirez@sebc-vm2 tmp]$ sudo wget https://github.com/DanielRamirezSanchez/SEBC/archive/master.zip
	--2018-10-16 12:28:32--  https://github.com/DanielRamirezSanchez/SEBC/archive/master.zip
	Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
	Connecting to github.com (github.com)|192.30.253.112|:443... connected.
	HTTP request sent, awaiting response... 302 Found
	Location: https://codeload.github.com/DanielRamirezSanchez/SEBC/zip/master [following]
	--2018-10-16 12:28:32--  https://codeload.github.com/DanielRamirezSanchez/SEBC/zip/master
	Resolving codeload.github.com (codeload.github.com)... 192.30.253.120, 192.30.253.121
	Connecting to codeload.github.com (codeload.github.com)|192.30.253.120|:443... connected.
	HTTP request sent, awaiting response... 200 OK
	Length: unspecified [application/zip]
	Saving to: ‘master.zip’

	    [   <=>                                                                                                                                              ] 1,834,838   3.02MB/s   in 0.6s

	2018-10-16 12:28:33 (3.02 MB/s) - ‘master.zip’ saved [1834838]

Creating destination folder

	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -put /tmp/master.zip /storageLab/precious/

Through CM I made the folder snapshottable

Remove the file

	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -rm /storageLab/precious/master.zip
	18/10/16 12:31:18 INFO fs.TrashPolicyDefault: Moved: 'hdfs://sebc-vm2.westeurope.cloudapp.azure.com:8020/storageLab/precious/master.zip' to trash at: hdfs://sebc-vm2.westeurope.cloudapp.azure.com:8020/user/hdfs/.Trash/Current/storageLab/precious/master.zip

Remove the folder

	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -rmdir /storageLab/precious
	rmdir: The directory /storageLab/precious cannot be deleted since /storageLab/precious is snapshottable and already has snapshots

Which isnot possible, since the folder is snapshottable and contains the snapshot. Thus, deleting the folder we would delete the snapshots.

Restore the lost zip

	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -ls /storageLab/precious/
	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -ls /storageLab/precious/.snapshot
	Found 1 items
	drwxr-xr-x   - hdfs supergroup          0 2018-10-16 12:30 /storageLab/precious/.snapshot/sebc-hdfs-test
	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -ls /storageLab/precious/.snapshot/sebc-hdfs-test
	Found 1 items
	-rw-r--r--   2 hdfs supergroup    1834838 2018-10-16 12:28 /storageLab/precious/.snapshot/sebc-hdfs-test/master.zip
	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -cp /storageLab/precious/.snapshot/sebc-hdfs-test/master.zip /storageLab/precious/master.zip
	[daniramirez@sebc-vm2 tmp]$ sudo -u hdfs hdfs dfs -ls /storageLab/precious/
	Found 1 items
	-rw-r--r--   2 hdfs supergroup    1834838 2018-10-16 12:36 /storageLab/precious/master.zip