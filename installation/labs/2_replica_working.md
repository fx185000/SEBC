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
```

#3.Start the MySQL server
```
service mysqld start
```

#4.Set the MySQL root password

```
grep "password" /var/log/mysqld.log    --- get the temporary password

/usr/bin/mysql_secure_installation
```

#5.On the master MySQL node, grant replication privileges
```
mysql -uroot -p

CREATE USER 'repl'@'feng-xu-2.vpc.cloudera.com' IDENTIFIED BY 'Repl123~';
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'feng-xu-2.vpc.cloudera.com';
SET GLOBAL binlog_format = 'ROW';
FLUSH TABLES WITH READ LOCK;
```

#6. In a second terminal session, log into the MySQL master and show its status
```
mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+-------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |
+------------------+----------+--------------+------------------+-------------------+
| mysql-bin.000001 |    19024 |              |                  |                   |
+------------------+----------+--------------+------------------+-------------------+
1 row in set (0.00 sec)
```

#7.Login to the replica server and configure a connection to the master
```
mysql> CHANGE MASTER TO MASTER_HOST='feng-xu-1.vpc.cloudera.com', MASTER_USER='repl', MASTER_PASSWORD='Repl123~', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=19024 ;
Query OK, 0 rows affected, 2 warnings (0.02 sec)
```

#8.Initiate slave operations on the replica
```
mysql> start slave;
Query OK, 0 rows affected (0.00 sec)

mysql> show slave status \G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: feng-xu-1.vpc.cloudera.com
                  Master_User: repl
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000001
          Read_Master_Log_Pos: 56830
               Relay_Log_File: feng-xu-2-relay-bin.000002
                Relay_Log_Pos: 320
        Relay_Master_Log_File: mysql-bin.000001
             Slave_IO_Running: Yes
            Slave_SQL_Running: No
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 1146
                   Last_Error: Error executing row event: 'Table 'scm.CM_VERSION' doesn't exist'
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 19024
              Relay_Log_Space: 38337
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: NULL
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 1146
               Last_SQL_Error: Error executing row event: 'Table 'scm.CM_VERSION' doesn't exist'
  Replicate_Ignore_Server_Ids: 
             Master_Server_Id: 1
                  Master_UUID: 38645ab5-5537-11e7-9f21-0abde78ceab2
             Master_Info_File: /var/lib/mysql/master.info
                    SQL_Delay: 0
          SQL_Remaining_Delay: NULL
      Slave_SQL_Running_State: 
           Master_Retry_Count: 86400
                  Master_Bind: 
      Last_IO_Error_Timestamp: 
     Last_SQL_Error_Timestamp: 170619 23:31:07
               Master_SSL_Crl: 
           Master_SSL_Crlpath: 
           Retrieved_Gtid_Set: 
            Executed_Gtid_Set: 
                Auto_Position: 0
         Replicate_Rewrite_DB: 
                 Channel_Name: 
           Master_TLS_Version: 
1 row in set (0.00 sec)
```
