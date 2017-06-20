#1.MySQL installation on master node & slave node
```
wget http://repo.mysql.com/mysql57-community-release-el6-11.noarch.rpm
rpm -ivh mysql57-community-release-el6-11.noarch.rpm
yum update
yum install mysql-server
chkconfig mysqld on
```

#2.Update /etc/my.cnf
```
master node:
server-id=1
log-bin=mysql-bin

slave node:
server-id=2
log-bin=mysql-bin

#3.Start the MySQL server
```
service mysqld start
```

#4.Set the MySQL root password

```
grep "password" /var/log/mysqld.log    --- get the temporary password

/usr/bin/mysql_secure_installation
```

#5.Create replication user

mysql -uroot -p

CREATE USER 'repl'@'feng-xu-2.vpc.cloudera.com' IDENTIFIED BY 'Repl123~';
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'feng-xu-2.vpc.cloudera.com';
SET GLOBAL binlog_format = 'ROW';
FLUSH TABLES WITH READ LOCK;


