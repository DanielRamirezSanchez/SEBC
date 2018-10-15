1. Check vm.swappiness on all your nodes

	[daniramirez@SEBC-Cloudera-vm1 ~]$ cat /proc/sys/vm/swappiness
	1

2. Show the mount attributes of all volumes

	[daniramirez@SEBC-Cloudera-vm1 ~]$ cat /proc/mounts
	rootfs / rootfs rw 0 0
	sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
	proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
	devtmpfs /dev devtmpfs rw,nosuid,size=8197928k,nr_inodes=2049482,mode=755 0 0
	securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
	tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
	devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
	tmpfs /run tmpfs rw,nosuid,nodev,mode=755 0 0
	tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
	cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
	pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
	cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
	cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids 0 0
	cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
	cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
	cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpuacct,cpu 0 0
	cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_prio,net_cls 0 0
	cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
	cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
	cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
	cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
	configfs /sys/kernel/config configfs rw,relatime 0 0
	/dev/sda2 / xfs rw,relatime,attr2,inode64,noquota 0 0
	systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=647 0 0
	mqueue /dev/mqueue mqueue rw,relatime 0 0
	debugfs /sys/kernel/debug debugfs rw,relatime 0 0
	hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
	/dev/sda1 /boot ext4 rw,relatime,data=ordered 0 0
	binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
	tmpfs /run/user/996 tmpfs rw,nosuid,nodev,relatime,size=1641552k,mode=700,uid=996,gid=993 0 0
	tmpfs /run/user/997 tmpfs rw,nosuid,nodev,relatime,size=1641552k,mode=700,uid=997,gid=995 0 0
	/dev/sdb1 /mnt/resource ext4 rw,noatime,discard,data=ordered 0 0
	tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=1641552k,mode=700,uid=1000,gid=1000 0 0

3. Show the reserve space of any non-root, ext-based volumes

	[daniramirez@SEBC-Cloudera-vm1 ~]$ df -h
	Filesystem      Size  Used Avail Use% Mounted on
	/dev/sda2        50G  7.5G   43G  16% /
	devtmpfs        7.9G     0  7.9G   0% /dev
	tmpfs           7.9G     0  7.9G   0% /dev/shm
	tmpfs           7.9G  8.4M  7.9G   1% /run
	tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
	/dev/sda1       240M  133M   91M  60% /boot
	/dev/sdb1        32G  2.1G   28G   7% /mnt/resource
	tmpfs           1.6G     0  1.6G   0% /run/user/993
	tmpfs           1.6G     0  1.6G   0% /run/user/1000


4. Disable transparent hugepage support

	Modified sudo vi /etc/default/grub adding 'transparent_hugepage=never' at the end of the line:
		GRUB_CMDLINE_LINUX="serial=tty0 console=ttyS0 earlyprintk=ttyS0 rootdelay=300 numa=off transparent_hugepage=never"

	[daniramirez@SEBC-Cloudera-vm1 ~]$ cat /sys/kernel/mm/transparent_hugepage/enabled
	always madvise [never]

5. List your network interface configuration

	[daniramirez@SEBC-Cloudera-vm1 ~]$ ifconfig
	eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
	        inet 10.0.2.5  netmask 255.255.255.0  broadcast 10.0.2.255
	        ether 00:0d:3a:3a:6f:43  txqueuelen 1000  (Ethernet)
	        RX packets 582896  bytes 826319741 (788.0 MiB)
	        RX errors 0  dropped 0  overruns 0  frame 0
	        TX packets 50037  bytes 9652932 (9.2 MiB)
	        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

	lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
	        inet 127.0.0.1  netmask 255.0.0.0
	        loop  txqueuelen 1  (Local Loopback)
	        RX packets 167797  bytes 114660414 (109.3 MiB)
	        RX errors 0  dropped 0  overruns 0  frame 0
	        TX packets 167797  bytes 114660414 (109.3 MiB)
	        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


6. List forward and reverse host lookups using getent or nslookup

	[daniramirez@SEBC-Cloudera-vm1 ~]$ getent hosts sebc-vm1.westeurope.cloudapp.azure.com
	10.0.2.5        sebc-vm1.westeurope.cloudapp.azure.com SEBC-Cloudera-vm1

	[daniramirez@SEBC-Cloudera-vm1 ~]$ nslookup sebc-vm1.westeurope.cloudapp.azure.com
	Server:         168.63.129.16
	Address:        168.63.129.16#53

	Non-authoritative answer:
	Name:   sebc-vm1.westeurope.cloudapp.azure.com
	Address: 168.63.27.141


	[daniramirez@SEBC-Cloudera-vm1 ~]$ getent hosts 10.0.2.5
	10.0.2.5        sebc-vm1.westeurope.cloudapp.azure.com SEBC-Cloudera-vm1

7. Show the nscd service is running

	sudo yum install nscd
	sudo systemctl enable nscd.service

	[daniramirez@SEBC-Cloudera-vm1 ~]$ service nscd status
	Redirecting to /bin/systemctl status nscd.service
	● nscd.service - Name Service Cache Daemon
	   Loaded: loaded (/usr/lib/systemd/system/nscd.service; enabled; vendor preset: disabled)
	   Active: active (running) since Mon 2018-10-15 18:12:48 UTC; 1h 2min ago
	 Main PID: 553 (nscd)
	   CGroup: /system.slice/nscd.service
	           └─553 /usr/sbin/nscd


8. Show the ntpd service is running

	sudo yum -y install ntp
	sudo systemctl stop chronyd.service
	sudo systemctl disable chronyd.service
	sudo systemctl start ntpd

	[daniramirez@SEBC-Cloudera-vm1 ~]$ systemctl status ntpd
	● ntpd.service - Network Time Service
	   Loaded: loaded (/usr/lib/systemd/system/ntpd.service; enabled; vendor preset: disabled)
	   Active: active (running) since Mon 2018-10-15 13:58:11 UTC; 1min 8s ago
	 Main PID: 24196 (ntpd)
	   CGroup: /system.slice/ntpd.service
	           └─24196 /usr/sbin/ntpd -u ntp:ntp -g

