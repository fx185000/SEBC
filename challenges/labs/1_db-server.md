#1.A command and output that shows the hostname of your database server
```
[root@fx185000-1 java]# hostname -a
fx185000-1
```

#2.A command and output that reports the database server version
```
[root@fx185000-1 java]# mysql -uroot -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 5.6.36 MySQL Community Server (GPL)
```

#3.A command and output that lists all the databases in the server
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hue                |
| metastore          |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
+--------------------+
8 rows in set (0.00 sec)
```