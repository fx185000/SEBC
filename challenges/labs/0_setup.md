#1.List the cloud provider you are using (AWS, GCE, Azure, CloudCat, other)
```
AWS:
m3.xlarge
ami-0d98813d
```

#2.List your instances by IP address and DNS name (don't use /etc/hosts for this)
```
fx185000-1.vpc.cloudera.com	fx185000-1	172.28.199.152	us-west-2/i-0410fcf7fe5935ff6
fx185000-2.vpc.cloudera.com	fx185000-2	172.28.194.140	us-west-2/i-0b63292b43d821ba7
fx185000-3.vpc.cloudera.com	fx185000-3	172.28.196.102	us-west-2/i-043a7b24571a11559
fx185000-4.vpc.cloudera.com	fx185000-4	172.28.197.187	us-west-2/i-0ee6e63542415dbd8
fx185000-5.vpc.cloudera.com	fx185000-5	172.28.192.90	us-west-2/i-02c40e43bd15b8876
```

#3.List the Linux release you are using
```
[root@fx185000-1 ~]# cat /etc/redhat-release
CentOS release 6.6 (Final)
```
#4.List the file system capacity for the first node
```
[root@fx185000-1 ~]# df -m  -v
Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/xvda1         30238  1505     27199   6% /
none                7442     0      7442   0% /dev/shm
/dev/xvdb          38374    33     38342   1% /data
/dev/xvdc          38374    33     38342   1% /data1
```

#5.List the command and output for yum repolist enabled
```
root@fx185000-1 ~]# yum repolist enabled
Loaded plugins: security
repo id              repo name                                            status
centos-base          Local Mirror CentOS-6 - Base                          6,518
centos-extras        Local Mirror CentOS-6 - Extras                           38
centos-updates       Local Mirror CentOS-6 - Updates                       1,370
epel                 Extra Packages for Enterprise Linux 6 - x86_64       12,344
repolist: 20,270
```
