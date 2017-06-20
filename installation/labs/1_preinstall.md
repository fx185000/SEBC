#1. enabling ssh without authenticate
```
Fengs-MacPro:~ feng.xu$ ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/feng.xu/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/feng.xu/.ssh/id_rsa.
Your public key has been saved in /Users/feng.xu/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:o3mnnR90xk7TJYfqboJPM9AuMhua7iSPXGQPnRikgxQ feng.xu@Fengs-MacPro.local
The key's randomart image is:
+---[RSA 2048]----+
| E. .            |
|.. o           . |
|. o .         o o|
|   . + . .   o +.|
|    = o S . o * .|
|   o o o + o = . |
|  . o B o.* o .  |
| . * o *.*.=..   |
|  oo* . ..++o    |
+----[SHA256]-----+

Fengs-MacPro:~ feng.xu$ ssh-copy-id root@feng-xu-1.vpc.cloudera.com
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/Users/feng.xu/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@feng-xu-1.vpc.cloudera.com's password: 

Number of key(s) added:        1

Now try logging into the machine, with:   "ssh 'root@feng-xu-1.vpc.cloudera.com'"
and check to make sure that only the key(s) you wanted were added.
```

#2.Check vm.swappiness on all your nodes
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "sysctl vm.swappiness"
commandline: ssh root@feng-xu-1.vpc.cloudera.com sysctl vm.swappiness ...
vm.swappiness = 0
commandline: ssh root@feng-xu-2.vpc.cloudera.com sysctl vm.swappiness ...
vm.swappiness = 0
commandline: ssh root@feng-xu-3.vpc.cloudera.com sysctl vm.swappiness ...
vm.swappiness = 0
commandline: ssh root@feng-xu-4.vpc.cloudera.com sysctl vm.swappiness ...
vm.swappiness = 0
commandline: ssh root@feng-xu-5.vpc.cloudera.com sysctl vm.swappiness ...
vm.swappiness = 0
```

#3.Show the mount attributes of your volume(s)
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "mount -v"
commandline: ssh root@feng-xu-1.vpc.cloudera.com mount -v ...
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cm_processes on /var/run/cloudera-scm-agent/process type tmpfs (rw,mode=0751)
commandline: ssh root@feng-xu-2.vpc.cloudera.com mount -v ...
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cm_processes on /var/run/cloudera-scm-agent/process type tmpfs (rw,mode=0751)
commandline: ssh root@feng-xu-3.vpc.cloudera.com mount -v ...
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cm_processes on /var/run/cloudera-scm-agent/process type tmpfs (rw,mode=0751)
commandline: ssh root@feng-xu-4.vpc.cloudera.com mount -v ...
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cm_processes on /var/run/cloudera-scm-agent/process type tmpfs (rw,mode=0751)
commandline: ssh root@feng-xu-5.vpc.cloudera.com mount -v ...
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
cm_processes on /var/run/cloudera-scm-agent/process type tmpfs (rw,mode=0751)
```

#4.If you have ext-based volumes, list the reserve space setting
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "df -m |grep /dev/xvda1"
commandline: ssh root@feng-xu-1.vpc.cloudera.com df -m |grep /dev/xvda1 ...
/dev/xvda1        251855 12711    226348   6% /
commandline: ssh root@feng-xu-2.vpc.cloudera.com df -m |grep /dev/xvda1 ...
/dev/xvda1        251855  8709    230350   4% /
commandline: ssh root@feng-xu-3.vpc.cloudera.com df -m |grep /dev/xvda1 ...
/dev/xvda1        251855  7741    231318   4% /
commandline: ssh root@feng-xu-4.vpc.cloudera.com df -m |grep /dev/xvda1 ...
/dev/xvda1        251855  7778    231281   4% /
commandline: ssh root@feng-xu-5.vpc.cloudera.com df -m |grep /dev/xvda1 ...
/dev/xvda1        251855  7835    231223   4% /
```

#5.Disable transparent hugepage support
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "echo never > /sys/kernel/mm/transparent_hugepage/enabled"
commandline: ssh root@feng-xu-1.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/enabled ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/enabled ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/enabled ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/enabled ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/enabled ...

Fengs-MacPro:~ feng.xu$ ./runall.sh "cat /sys/kernel/mm/transparent_hugepage/enabled"
commandline: ssh root@feng-xu-1.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/enabled ...
always madvise [never]
commandline: ssh root@feng-xu-2.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/enabled ...
always madvise [never]
commandline: ssh root@feng-xu-3.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/enabled ...
always madvise [never]
commandline: ssh root@feng-xu-4.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/enabled ...
always madvise [never]
commandline: ssh root@feng-xu-5.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/enabled ...
always madvise [never]

Fengs-MacPro:~ feng.xu$ ./runall.sh "echo never > /sys/kernel/mm/transparent_hugepage/defrag"
commandline: ssh root@feng-xu-1.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/defrag ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/defrag ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/defrag ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/defrag ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com echo never > /sys/kernel/mm/transparent_hugepage/defrag ...

Fengs-MacPro:~ feng.xu$ ./runall.sh "cat /sys/kernel/mm/transparent_hugepage/defrag"
commandline: ssh root@feng-xu-1.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/defrag ...
always madvise [never]
commandline: ssh root@feng-xu-2.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/defrag ...
always madvise [never]
commandline: ssh root@feng-xu-3.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/defrag ...
always madvise [never]
commandline: ssh root@feng-xu-4.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/defrag ...
always madvise [never]
commandline: ssh root@feng-xu-5.vpc.cloudera.com cat /sys/kernel/mm/transparent_hugepage/defrag ...
always madvise [never]
```

#6.List your network interface configuration
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "ip addr"
commandline: ssh root@feng-xu-1.vpc.cloudera.com ip addr ...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP qlen 1000
    link/ether 0a:bd:e7:8c:ea:b2 brd ff:ff:ff:ff:ff:ff
    inet 172.28.210.128/21 brd 172.28.215.255 scope global eth0
    inet6 fe80::8bd:e7ff:fe8c:eab2/64 scope link 
       valid_lft forever preferred_lft forever
commandline: ssh root@feng-xu-2.vpc.cloudera.com ip addr ...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP qlen 1000
    link/ether 0a:3b:02:ba:83:2a brd ff:ff:ff:ff:ff:ff
    inet 172.28.211.85/21 brd 172.28.215.255 scope global eth0
    inet6 fe80::83b:2ff:feba:832a/64 scope link 
       valid_lft forever preferred_lft forever
commandline: ssh root@feng-xu-3.vpc.cloudera.com ip addr ...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP qlen 1000
    link/ether 06:07:49:be:71:5c brd ff:ff:ff:ff:ff:ff
    inet 172.28.193.196/21 brd 172.28.199.255 scope global eth0
    inet6 fe80::407:49ff:febe:715c/64 scope link 
       valid_lft forever preferred_lft forever
commandline: ssh root@feng-xu-4.vpc.cloudera.com ip addr ...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP qlen 1000
    link/ether 06:91:cd:7e:c1:a8 brd ff:ff:ff:ff:ff:ff
    inet 172.28.198.163/21 brd 172.28.199.255 scope global eth0
    inet6 fe80::491:cdff:fe7e:c1a8/64 scope link 
       valid_lft forever preferred_lft forever
commandline: ssh root@feng-xu-5.vpc.cloudera.com ip addr ...
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP qlen 1000
    link/ether 06:41:32:f8:48:e4 brd ff:ff:ff:ff:ff:ff
    inet 172.28.197.155/21 brd 172.28.199.255 scope global eth0
    inet6 fe80::441:32ff:fef8:48e4/64 scope link 
       valid_lft forever preferred_lft forever
```

#7.Show that forward and reverse host lookups are correctly resolved
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "getent hosts"
commandline: ssh root@feng-xu-1.vpc.cloudera.com getent hosts ...
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
commandline: ssh root@feng-xu-2.vpc.cloudera.com getent hosts ...
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
commandline: ssh root@feng-xu-3.vpc.cloudera.com getent hosts ...
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
commandline: ssh root@feng-xu-4.vpc.cloudera.com getent hosts ...
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
commandline: ssh root@feng-xu-5.vpc.cloudera.com getent hosts ...
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6

[root@feng-xu-1 ~]# nslookup `hostname`
Server:		10.17.181.104
Address:	10.17.181.104#53

Name:	feng-xu-1.vpc.cloudera.com
Address: 172.28.210.128
```

#8.Show the nscd service is running
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "service nscd status"
commandline: ssh root@feng-xu-1.vpc.cloudera.com service nscd status ...
nscd (pid 1349) is running...
commandline: ssh root@feng-xu-2.vpc.cloudera.com service nscd status ...
nscd (pid 1353) is running...
commandline: ssh root@feng-xu-3.vpc.cloudera.com service nscd status ...
nscd (pid 6249) is running...
commandline: ssh root@feng-xu-4.vpc.cloudera.com service nscd status ...
nscd (pid 6278) is running...
commandline: ssh root@feng-xu-5.vpc.cloudera.com service nscd status ...
nscd (pid 6284) is running...
```

#9.Show the ntpd service is running
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "service ntpd status"
commandline: ssh root@feng-xu-1.vpc.cloudera.com service ntpd status ...
ntpd (pid  1486) is running...
commandline: ssh root@feng-xu-2.vpc.cloudera.com service ntpd status ...
ntpd (pid  1483) is running...
commandline: ssh root@feng-xu-3.vpc.cloudera.com service ntpd status ...
ntpd (pid  2019) is running...
commandline: ssh root@feng-xu-4.vpc.cloudera.com service ntpd status ...
ntpd (pid  2028) is running...
commandline: ssh root@feng-xu-5.vpc.cloudera.com service ntpd status ...
ntpd (pid  2013) is running...
```



