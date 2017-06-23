#1.The first line of the server log
```
[root@fx185000-2 parcel]# head -1 /var/log/cloudera-scm-server/cloudera-scm-server.log
2017-06-23 10:07:43,529 INFO main:com.cloudera.server.cmf.Main: Starting SCM Server. JVM Args: [-Dlog4j.configuration=file:/etc/cloudera-scm-server/log4j.properties, -Dfile.encoding=UTF-8, -Dcmf.root.logger=INFO,LOGFILE, -Dcmf.log.dir=/var/log/cloudera-scm-server, -Dcmf.log.file=cloudera-scm-server.log, -Dcmf.jetty.threshhold=WARN, -Dcmf.schema.dir=/usr/share/cmf/schema, -Djava.awt.headless=true, -Djava.net.preferIPv4Stack=true, -Dpython.home=/usr/share/cmf/python, -XX:+UseConcMarkSweepGC, -XX:+UseParNewGC, -XX:+HeapDumpOnOutOfMemoryError, -Xmx2G, -XX:MaxPermSize=256m, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=/tmp, -XX:OnOutOfMemoryError=kill -9 %p], Args: [], Version: 5.11.1 (#9 built by jenkins on 20170525-1411 git: 8adcfb8545cb0a35f590717b2626a9ea04948dae)
```
#2.The line(s) that contain the phrase "Started Jetty server"
```
[root@fx185000-2 parcel]# grep "Started Jetty server" /var/log/cloudera-scm-server/cloudera-scm-server.log
2017-06-23 10:09:09,665 INFO WebServerImpl:com.cloudera.server.cmf.WebServerImpl: Started Jetty server.
```
#3.The content of the db.properties file
```
[root@fx185000-2 parcel]# cat /etc/cloudera-scm-server/db.properties
# Auto-generated by scm_prepare_database.sh on Fri Jun 23 10:05:49 PDT 2017
#
# For information describing how to configure the Cloudera Manager Server
# to connect to databases, see the "Cloudera Manager Installation Guide."
#
com.cloudera.cmf.db.type=mysql
com.cloudera.cmf.db.host=fx185000-1.vpc.cloudera.com
com.cloudera.cmf.db.name=scm
com.cloudera.cmf.db.user=scm
com.cloudera.cmf.db.setupType=EXTERNAL
com.cloudera.cmf.db.password=scm123
```