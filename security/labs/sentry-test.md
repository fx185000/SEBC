
#1.Authenticate user fx185000 as a Kerberos principal
```
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
```

#2.Use beeline to confirm your principal sees no tables
```
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
```
#3.Use hive to create a sentry role with full authorization
```
[root@feng-xu-1 ~]# kinit -kt /tmp/hive.keytab hive@HADOOP.COM
[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 2ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> create role sentry_admin;
Error: Error while compiling statement: FAILED: SemanticException The current builtin authorization in Hive is incomplete and disabled. (state=42000,code=40000)

Using CM to enable the Sentry for Hive

[root@feng-xu-1 ~]# kinit -kt /tmp/hive.keytab hive@HADOOP.COM
[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 2ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> create role sentry_admin;
INFO  : Compiling command(queryId=hive_20170622005959_f416daa6-74d1-4a0b-b1ed-53497d7388a4): create role sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622005959_f416daa6-74d1-4a0b-b1ed-53497d7388a4); Time taken: 0.064 seconds
INFO  : Executing command(queryId=hive_20170622005959_f416daa6-74d1-4a0b-b1ed-53497d7388a4): create role sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622005959_f416daa6-74d1-4a0b-b1ed-53497d7388a4); Time taken: 0.144 seconds
INFO  : OK
No rows affected (0.262 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> grant all on server server1 to role sentry_admin;
INFO  : Compiling command(queryId=hive_20170622010202_149bfcd1-28c3-41ca-935f-92ed3872fe9e): grant all on server server1 to role sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622010202_149bfcd1-28c3-41ca-935f-92ed3872fe9e); Time taken: 0.082 seconds
INFO  : Executing command(queryId=hive_20170622010202_149bfcd1-28c3-41ca-935f-92ed3872fe9e): grant all on server server1 to role sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622010202_149bfcd1-28c3-41ca-935f-92ed3872fe9e); Time taken: 0.113 seconds
INFO  : OK
No rows affected (0.206 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> grant role sentry_admin to group hive;
INFO  : Compiling command(queryId=hive_20170622010202_56775bae-42b0-427e-802a-a6c1feb59e13): grant role sentry_admin to group hive
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622010202_56775bae-42b0-427e-802a-a6c1feb59e13); Time taken: 0.067 seconds
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> grant role sentry_admin to group fx185000;
INFO  : Compiling command(queryId=hive_20170622010303_1aa1030d-d936-441c-9673-7ca065d06219): grant role sentry_admin to group fx185000
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622010303_1aa1030d-d936-441c-9673-7ca065d06219); Time taken: 0.056 seconds
INFO  : Executing command(queryId=hive_20170622010303_1aa1030d-d936-441c-9673-7ca065d06219): grant role sentry_admin to group fx185000
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622010303_1aa1030d-d936-441c-9673-7ca065d06219); Time taken: 0.058 seconds
INFO  : OK
No rows affected (0.129 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> !quit
Closing: 0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
```

#4.The above statement should now return all tables
```
[root@feng-xu-1 ~]# kinit -kt /tmp/fx185000.keytab fx185000@HADOOP.COM
[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 2ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> show tables;
INFO  : Compiling command(queryId=hive_20170622010303_d95437bf-3102-4768-99fc-7cc011feb470): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170622010303_d95437bf-3102-4768-99fc-7cc011feb470); Time taken: 0.238 seconds
INFO  : Executing command(queryId=hive_20170622010303_d95437bf-3102-4768-99fc-7cc011feb470): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622010303_d95437bf-3102-4768-99fc-7cc011feb470); Time taken: 0.206 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.599 seconds)
```

#5.Create additional test users
```
feng.xu@Fengs-MacPro:~$ ./runall.sh "groupadd selector"
commandline: ssh root@feng-xu-1.vpc.cloudera.com groupadd selector ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com groupadd selector ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com groupadd selector ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com groupadd selector ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com groupadd selector ...
feng.xu@Fengs-MacPro:~$ ./runall.sh "groupadd inserters"
commandline: ssh root@feng-xu-1.vpc.cloudera.com groupadd inserters ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com groupadd inserters ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com groupadd inserters ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com groupadd inserters ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com groupadd inserters ...
feng.xu@Fengs-MacPro:~$ ./runall.sh "useradd -u 1100 -g selector george"
commandline: ssh root@feng-xu-1.vpc.cloudera.com useradd -u 1100 -g selector george ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com useradd -u 1100 -g selector george ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com useradd -u 1100 -g selector george ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com useradd -u 1100 -g selector george ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com useradd -u 1100 -g selector george ...
feng.xu@Fengs-MacPro:~$ ./runall.sh "useradd -u 1200 -g inserters ferdinand"
commandline: ssh root@feng-xu-1.vpc.cloudera.com useradd -u 1200 -g inserters ferdinand ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com useradd -u 1200 -g inserters ferdinand ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com useradd -u 1200 -g inserters ferdinand ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com useradd -u 1200 -g inserters ferdinand ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com useradd -u 1200 -g inserters ferdinand ...


[root@feng-xu-1 ~]# kadmin.local
Authenticating as principal root/admin@HADOOP.COM with password.
kadmin.local:  addprinc -pw george george@HADOOP.COM
WARNING: no policy specified for george@HADOOP.COM; defaulting to no policy
Principal "george@HADOOP.COM" created.
kadmin.local:  ktadd -k /tmp/george.keytab george@HADOOP.COM
Entry for principal george@HADOOP.COM with kvno 2, encryption type aes256-cts-hmac-sha1-96 added to keytab WRFILE:/tmp/george.keytab.
Entry for principal george@HADOOP.COM with kvno 2, encryption type aes128-cts-hmac-sha1-96 added to keytab WRFILE:/tmp/george.keytab.
Entry for principal george@HADOOP.COM with kvno 2, encryption type des3-cbc-sha1 added to keytab WRFILE:/tmp/george.keytab.
Entry for principal george@HADOOP.COM with kvno 2, encryption type arcfour-hmac added to keytab WRFILE:/tmp/george.keytab.
Entry for principal george@HADOOP.COM with kvno 2, encryption type des-hmac-sha1 added to keytab WRFILE:/tmp/george.keytab.
Entry for principal george@HADOOP.COM with kvno 2, encryption type des-cbc-md5 added to keytab WRFILE:/tmp/george.keytab.
kadmin.local:  addprinc -pw ferdinand ferdinand@HADOOP.COM
WARNING: no policy specified for ferdinand@HADOOP.COM; defaulting to no policy
Principal "ferdinand@HADOOP.COM" created.
kadmin.local:  ktadd -k /tmp/ferdinand.keytab ferdinand@HADOOP.COM
Entry for principal ferdinand@HADOOP.COM with kvno 2, encryption type aes256-cts-hmac-sha1-96 added to keytab WRFILE:/tmp/ferdinand.keytab.
Entry for principal ferdinand@HADOOP.COM with kvno 2, encryption type aes128-cts-hmac-sha1-96 added to keytab WRFILE:/tmp/ferdinand.keytab.
Entry for principal ferdinand@HADOOP.COM with kvno 2, encryption type des3-cbc-sha1 added to keytab WRFILE:/tmp/ferdinand.keytab.
Entry for principal ferdinand@HADOOP.COM with kvno 2, encryption type arcfour-hmac added to keytab WRFILE:/tmp/ferdinand.keytab.
Entry for principal ferdinand@HADOOP.COM with kvno 2, encryption type des-hmac-sha1 added to keytab WRFILE:/tmp/ferdinand.keytab.
Entry for principal ferdinand@HADOOP.COM with kvno 2, encryption type des-cbc-md5 added to keytab WRFILE:/tmp/ferdinand.keytab.
kadmin.local:  exit
```
#6.Create test roles & Grant privilege
```
[root@feng-xu-1 ~]# kinit -kt /tmp/hive.keytab hive@HADOOP.COM
[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 1ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> create role reads;
INFO  : Compiling command(queryId=hive_20170622011414_b52a8c7a-8ba4-4237-9f84-a53eb5feda23): create role reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011414_b52a8c7a-8ba4-4237-9f84-a53eb5feda23); Time taken: 0.07 seconds
INFO  : Executing command(queryId=hive_20170622011414_b52a8c7a-8ba4-4237-9f84-a53eb5feda23): create role reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011414_b52a8c7a-8ba4-4237-9f84-a53eb5feda23); Time taken: 0.044 seconds
INFO  : OK
No rows affected (0.165 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> create role writes;
INFO  : Compiling command(queryId=hive_20170622011414_44a815a3-3ce4-4828-ba21-43664975676c): create role writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011414_44a815a3-3ce4-4828-ba21-43664975676c); Time taken: 0.055 seconds
INFO  : Executing command(queryId=hive_20170622011414_44a815a3-3ce4-4828-ba21-43664975676c): create role writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011414_44a815a3-3ce4-4828-ba21-43664975676c); Time taken: 0.028 seconds
INFO  : OK
No rows affected (0.094 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20170622011515_73cde7a2-3477-4841-8063-95f707209bac): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011515_73cde7a2-3477-4841-8063-95f707209bac); Time taken: 0.079 seconds
INFO  : Executing command(queryId=hive_20170622011515_73cde7a2-3477-4841-8063-95f707209bac): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011515_73cde7a2-3477-4841-8063-95f707209bac); Time taken: 0.047 seconds
INFO  : OK
No rows affected (0.137 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20170622011515_48d662e3-3315-46e2-81c9-3d7887d294c6): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011515_48d662e3-3315-46e2-81c9-3d7887d294c6); Time taken: 0.052 seconds
INFO  : Executing command(queryId=hive_20170622011515_48d662e3-3315-46e2-81c9-3d7887d294c6): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011515_48d662e3-3315-46e2-81c9-3d7887d294c6); Time taken: 0.03 seconds
INFO  : OK
No rows affected (0.093 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20170622011515_64f57b6c-f1bc-4eca-9eb2-b0a3ac8ca2f8): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011515_64f57b6c-f1bc-4eca-9eb2-b0a3ac8ca2f8); Time taken: 0.051 seconds
INFO  : Executing command(queryId=hive_20170622011515_64f57b6c-f1bc-4eca-9eb2-b0a3ac8ca2f8): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011515_64f57b6c-f1bc-4eca-9eb2-b0a3ac8ca2f8); Time taken: 0.092 seconds
INFO  : OK
No rows affected (0.156 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20170622011515_f02be186-012d-4519-b0cf-04319e06a3f9): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011515_f02be186-012d-4519-b0cf-04319e06a3f9); Time taken: 0.053 seconds
INFO  : Executing command(queryId=hive_20170622011515_f02be186-012d-4519-b0cf-04319e06a3f9): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011515_f02be186-012d-4519-b0cf-04319e06a3f9); Time taken: 0.061 seconds
INFO  : OK
No rows affected (0.127 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20170622011515_80d9e9d2-d4bc-41e1-976d-008064da9a71): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011515_80d9e9d2-d4bc-41e1-976d-008064da9a71); Time taken: 0.063 seconds
INFO  : Executing command(queryId=hive_20170622011515_80d9e9d2-d4bc-41e1-976d-008064da9a71): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011515_80d9e9d2-d4bc-41e1-976d-008064da9a71); Time taken: 0.036 seconds
INFO  : OK
No rows affected (0.111 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> !quit;
Unknown command: quit;
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> !quit
Closing: 0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
```

#7.Use beeline to test two principals
```
[root@feng-xu-1 ~]# kinit -kt /tmp/george.keytab george@HADOOP.COM
[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 2ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> show tables;
INFO  : Compiling command(queryId=hive_20170622011717_6672afb6-fc6d-4467-9e57-30c15608ff36): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011717_6672afb6-fc6d-4467-9e57-30c15608ff36); Time taken: 0.061 seconds
INFO  : Executing command(queryId=hive_20170622011717_6672afb6-fc6d-4467-9e57-30c15608ff36): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011717_6672afb6-fc6d-4467-9e57-30c15608ff36); Time taken: 0.119 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.272 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> !quit
Closing: 0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
[root@feng-xu-1 ~]# kinit -kt /tmp/ferdinand.keytab ferdinand@HADOOP.COM
[root@feng-xu-1 ~]# beeline -u "jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM"
scan complete in 2ms
Connecting to jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.1)
Driver: Hive JDBC (version 1.1.0-cdh5.9.1)
Transaction isolation: TRANSACTION_REPEATABLE_READ
Beeline version 1.1.0-cdh5.9.1 by Apache Hive
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> show tables;
INFO  : Compiling command(queryId=hive_20170622011818_53021dc3-4506-43f6-a44d-a6a770871c86): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170622011818_53021dc3-4506-43f6-a44d-a6a770871c86); Time taken: 0.06 seconds
INFO  : Executing command(queryId=hive_20170622011818_53021dc3-4506-43f6-a44d-a6a770871c86): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170622011818_53021dc3-4506-43f6-a44d-a6a770871c86); Time taken: 0.135 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.281 seconds)
0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10> !quit
Closing: 0: jdbc:hive2://feng-xu-1.vpc.cloudera.com:10000/default;principal=hive/feng-xu-1.vpc.cloudera.com@HADOOP.COM
```


