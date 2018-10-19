VMs deployed for the SEBC Challenge (October 19, 2018. Madrid)

	Cloud provider: Microsoft Azure

Instances external IPs and DNS names

	40.89.137.231	sebc-vm1-challenge.francecentral.cloudapp.azure.com
	40.89.140.118	sebc-vm2-challenge.francecentral.cloudapp.azure.com
	40.89.162.232	sebc-vm3-challenge.francecentral.cloudapp.azure.com
	40.89.163.210	sebc-vm4-challenge.francecentral.cloudapp.azure.com
	40.89.136.96	sebc-vm5-challenge.francecentral.cloudapp.azure.com

Chosen Linux release

	[daniramirez@sebc-vm1-challenges ~]$ cat /etc/redhat-release
	CentOS Linux release 7.2.1511 (Core)

Disk space on each node

	[daniramirez@sebc-vm1-challenges ~]$ df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        50G  1.3G   49G   3% /
	devtmpfs        7.9G     0  7.9G   0% /dev
	tmpfs           7.9G     0  7.9G   0% /dev/shm
	tmpfs           7.9G  8.3M  7.9G   1% /run
	tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
	/dev/sda1       240M  124M  100M  56% /boot
	/dev/sdb1        32G  2.1G   28G   7% /mnt/resource
	tmpfs           1.6G     0  1.6G   0% /run/user/1000

	[daniramirez@sebc-vm2-challenges ~]$ df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        50G  1.3G   49G   3% /
	devtmpfs        7.9G     0  7.9G   0% /dev
	tmpfs           7.9G     0  7.9G   0% /dev/shm
	tmpfs           7.9G  8.4M  7.9G   1% /run
	tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
	/dev/sda1       240M  124M  100M  56% /boot
	/dev/sdb1        32G  2.1G   28G   7% /mnt/resource
	tmpfs           1.6G     0  1.6G   0% /run/user/0
	tmpfs           1.6G     0  1.6G   0% /run/user/1000

	[daniramirez@sebc-vm3-challenges ~]$  df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        50G  1.3G   49G   3% /
	devtmpfs        7.9G     0  7.9G   0% /dev
	tmpfs           7.9G     0  7.9G   0% /dev/shm
	tmpfs           7.9G  8.3M  7.9G   1% /run
	tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
	/dev/sda1       240M  124M  100M  56% /boot
	/dev/sdb1        32G  2.1G   28G   7% /mnt/resource
	tmpfs           1.6G     0  1.6G   0% /run/user/1000

	[daniramirez@sebc-vm4-challenges ~]$  df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        50G  1.3G   49G   3% /
	devtmpfs        7.9G     0  7.9G   0% /dev
	tmpfs           7.9G     0  7.9G   0% /dev/shm
	tmpfs           7.9G  8.3M  7.9G   1% /run
	tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
	/dev/sda1       240M  124M  100M  56% /boot
	/dev/sdb1        32G  2.1G   28G   7% /mnt/resource
	tmpfs           1.6G     0  1.6G   0% /run/user/1000

	[daniramirez@sebc-vm5-challenges ~]$  df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        50G  1.3G   49G   3% /
	devtmpfs        7.9G     0  7.9G   0% /dev
	tmpfs           7.9G     0  7.9G   0% /dev/shm
	tmpfs           7.9G  8.4M  7.9G   1% /run
	tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
	/dev/sda1       240M  124M  100M  56% /boot
	/dev/sdb1        32G  2.1G   28G   7% /mnt/resource
	tmpfs           1.6G     0  1.6G   0% /run/user/0
	tmpfs           1.6G     0  1.6G   0% /run/user/1000

Yum repolist command output

	[daniramirez@sebc-vm1-challenges ~]$ yum repolist enabled
	Loaded plugins: fastestmirror
	Loading mirror speeds from cached hostfile
	repo id                               repo name                                                      status
	base/x86_64                           CentOS-7 - Base                                                9,911
	extras/7/x86_64                       CentOS-7 - Extras                                                432
	openlogic/x86_64                      CentOS-7 - openlogic packages for x86_64                         115
	updates/x86_64                        CentOS-7 - Updates                                             1,561
	repolist: 12,019

User list

	[daniramirez@sebc-vm1-challenges ~]$ cat /etc/passwd
	root:x:0:0:root:/root:/bin/bash
	bin:x:1:1:bin:/bin:/sbin/nologin
	daemon:x:2:2:daemon:/sbin:/sbin/nologin
	adm:x:3:4:adm:/var/adm:/sbin/nologin
	lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
	sync:x:5:0:sync:/sbin:/bin/sync
	shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
	halt:x:7:0:halt:/sbin:/sbin/halt
	mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
	operator:x:11:0:operator:/root:/sbin/nologin
	games:x:12:100:games:/usr/games:/sbin/nologin
	ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
	nobody:x:99:99:Nobody:/:/sbin/nologin
	avahi-autoipd:x:170:170:Avahi IPv4LL Stack:/var/lib/avahi-autoipd:/sbin/nologin
	systemd-bus-proxy:x:999:997:systemd Bus Proxy:/:/sbin/nologin
	systemd-network:x:998:996:systemd Network Management:/:/sbin/nologin
	dbus:x:81:81:System message bus:/:/sbin/nologin
	polkitd:x:997:995:User for polkitd:/:/sbin/nologin
	tss:x:59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
	postfix:x:89:89::/var/spool/postfix:/sbin/nologin
	sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
	chrony:x:996:994::/var/lib/chrony:/sbin/nologin
	daniramirez:x:1000:1000::/home/daniramirez:/bin/bash
	raffles:x:2000:1001::/home/raffles:/bin/bash
	fullerton:x:3000:1002::/home/fullerton:/bin/bash

Group list

	[daniramirez@sebc-vm1-challenges ~]$ cat /etc/group
	root:x:0:
	bin:x:1:
	daemon:x:2:
	sys:x:3:
	adm:x:4:
	tty:x:5:
	disk:x:6:
	lp:x:7:
	mem:x:8:
	kmem:x:9:
	wheel:x:10:
	cdrom:x:11:
	mail:x:12:postfix
	man:x:15:
	dialout:x:18:
	floppy:x:19:
	games:x:20:
	tape:x:30:
	video:x:39:
	ftp:x:50:
	lock:x:54:
	audio:x:63:
	nobody:x:99:
	users:x:100:
	avahi-autoipd:x:170:
	utmp:x:22:
	utempter:x:35:
	ssh_keys:x:999:
	input:x:998:
	systemd-journal:x:190:
	systemd-bus-proxy:x:997:
	systemd-network:x:996:
	dbus:x:81:
	polkitd:x:995:
	dip:x:40:
	tss:x:59:
	postdrop:x:90:
	postfix:x:89:
	sshd:x:74:
	chrony:x:994:
	daniramirez:x:1000:
	shops:x:1001:
	hotels:x:1002:
