
[root@feng-xu-1 ~]# kadmin.local
Authenticating as principal root/admin@HADOOP.COM with password.
kadmin.local:  addprinc -pw fx185000 fx185000@HADOOP.COM
WARNING: no policy specified for fx185000@HADOOP.COM; defaulting to no policy
add_principal: Principal or policy already exists while creating "fx185000@HADOOP.COM".
kadmin.local:  ktadd -k /tmp/fx185000.keytab fx185000@HADOOP.COM
Entry for principal fx185000@HADOOP.COM with kvno 2, encryption type aes256-cts-hmac-sha1-96 added to keytab WRFILE:/tmp/fx185000.keytab.
Entry for principal fx185000@HADOOP.COM with kvno 2, encryption type aes128-cts-hmac-sha1-96 added to keytab WRFILE:/tmp/fx185000.keytab.
Entry for principal fx185000@HADOOP.COM with kvno 2, encryption type des3-cbc-sha1 added to keytab WRFILE:/tmp/fx185000.keytab.
Entry for principal fx185000@HADOOP.COM with kvno 2, encryption type arcfour-hmac added to keytab WRFILE:/tmp/fx185000.keytab.
Entry for principal fx185000@HADOOP.COM with kvno 2, encryption type des-hmac-sha1 added to keytab WRFILE:/tmp/fx185000.keytab.
Entry for principal fx185000@HADOOP.COM with kvno 2, encryption type des-cbc-md5 added to keytab WRFILE:/tmp/fx185000.keytab.
kadmin.local:  exit

[root@feng-xu-1 ~]# kinit -kt /tmp/fx185000.keytab fx185000@HADOOP.COM

[root@feng-xu-1 ~]# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: fx185000@HADOOP.COM

Valid starting     Expires            Service principal
06/22/17 00:13:54  06/23/17 00:13:54  krbtgt/HADOOP.COM@HADOOP.COM
	renew until 06/29/17 00:13:54

[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 1ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> show databases;
INFO  : Compiling command(queryId=hive_20170622001616_c19edd92-cc05-443d-9344-94bbdab0c55e): show databases
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:database_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170622001616_c19edd92-cc05-443d-9344-94bbdab0c55e); Time taken: 0.009 seconds
INFO  : Executing command(queryId=hive_20170622001616_c19edd92-cc05-443d-9344-94bbdab0c55e): show databases
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622001616_c19edd92-cc05-443d-9344-94bbdab0c55e); Time taken: 0.028 seconds
INFO  : OK
+----------------+--+
| database_name  |
+----------------+--+
| default        |
+----------------+--+
1 row selected (0.125 seconds)


