##1.Choose a partner in class
```
add a peer using CM: http://dfadeyev-1.gce.cloudera.com:7180
```

##2.Name a source directory after your GitHub handle
```
[hdfs@feng-xu-1 ~]$ hdfs dfs -mkdir /labs
[hdfs@feng-xu-1 ~]$ hdfs dfs -mkdir /labs/storage
```

##3.Name a target directory after your partner's GitHub handle
```
[hdfs@feng-xu-1 ~]$ hdfs dfs -mkdir /labs/storage/dest
```

##4.Use teragen to create a 500 MB file
```
[hdfs@feng-xu-1 ~]$ hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 5242880 /labs/storage/file500MB
17/06/20 10:43:40 INFO client.RMProxy: Connecting to ResourceManager at feng-xu-1.vpc.cloudera.com/172.28.210.128:8032
17/06/20 10:43:40 INFO terasort.TeraSort: Generating 5242880 using 4
17/06/20 10:43:40 INFO mapreduce.JobSubmitter: number of splits:4
17/06/20 10:43:40 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/06/20 10:43:40 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1497920647653_0001
17/06/20 10:43:41 INFO impl.YarnClientImpl: Submitted application application_1497920647653_0001
17/06/20 10:43:41 INFO mapreduce.Job: The url to track the job: http://feng-xu-1.vpc.cloudera.com:8088/proxy/application_1497920647653_0001/
17/06/20 10:43:41 INFO mapreduce.Job: Running job: job_1497920647653_0001
17/06/20 10:43:47 INFO mapreduce.Job: Job job_1497920647653_0001 running in uber mode : false
17/06/20 10:43:47 INFO mapreduce.Job:  map 0% reduce 0%
17/06/20 10:43:56 INFO mapreduce.Job:  map 25% reduce 0%
17/06/20 10:43:57 INFO mapreduce.Job:  map 100% reduce 0%
17/06/20 10:43:58 INFO mapreduce.Job: Job job_1497920647653_0001 completed successfully
17/06/20 10:43:58 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=490500
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=337
		HDFS: Number of bytes written=524288000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=31393
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=31393
		Total vcore-seconds taken by all map tasks=31393
		Total megabyte-seconds taken by all map tasks=32146432
	Map-Reduce Framework
		Map input records=5242880
		Map output records=5242880
		Input split bytes=337
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=531
		CPU time spent (ms)=19840
		Physical memory (bytes) snapshot=1373110272
		Virtual memory (bytes) snapshot=6284423168
		Total committed heap usage (bytes)=1801453568
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=11257830824958050
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=524288000

[hdfs@feng-xu-1 ~]$ hdfs dfs -ls /labs/storage/file500MB
Found 5 items
-rw-r--r--   3 hdfs supergroup          0 2017-06-20 10:43 /labs/storage/file500MB/_SUCCESS
-rw-r--r--   3 hdfs supergroup  131072000 2017-06-20 10:43 /labs/storage/file500MB/part-m-00000
-rw-r--r--   3 hdfs supergroup  131072000 2017-06-20 10:43 /labs/storage/file500MB/part-m-00001
-rw-r--r--   3 hdfs supergroup  131072000 2017-06-20 10:43 /labs/storage/file500MB/part-m-00002
-rw-r--r--   3 hdfs supergroup  131072000 2017-06-20 10:43 /labs/storage/file500MB/part-m-00003

```

##5.Copy your partner's file to your target directory
using BDR

##6.Browse the results
```
[hdfs@feng-xu-1 ~]$ hdfs dfs -ls /labs/storage/dest
Found 1 items
-rw-r--r--   3 dfadeyev dfadeyev  524288000 2017-06-20 10:51 /labs/storage/dest/part-m-00000

[hdfs@feng-xu-1 ~]$ hdfs fsck /labs/storage/dest/part-m-00000 -files -blocks
Connecting to namenode via http://feng-xu-1.vpc.cloudera.com:50070
FSCK started by hdfs (auth:SIMPLE) from /172.28.210.128 for path /labs/storage/dest/part-m-00000 at Tue Jun 20 11:18:15 PDT 2017
/labs/storage/dest/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-1192758595-172.28.210.128-1497920591148:blk_1073743567_2743 len=134217728 Live_repl=3
1. BP-1192758595-172.28.210.128-1497920591148:blk_1073743576_2752 len=134217728 Live_repl=3
2. BP-1192758595-172.28.210.128-1497920591148:blk_1073743581_2757 len=134217728 Live_repl=3
3. BP-1192758595-172.28.210.128-1497920591148:blk_1073743582_2758 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	0
 Total files:	1
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		4
 Number of racks:		1
FSCK ended at Tue Jun 20 11:18:15 PDT 2017 in 1 milliseconds


The filesystem under path '/labs/storage/dest/part-m-00000' is HEALTHY
```


get the orginal file information from the partner:
```
root@dfadeyev-1:~# sudo -uhdfs hdfs fsck /user/dfadeyev/dfadeyev/part-m-00000 -files -blocks
Connecting to namenode via http://dfadeyev-2.gce.cloudera.com:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.112.153 for path /user/dfadeyev/dfadeyev/part-m-00000 at Tue Jun 20 11:23:22 PDT 2017
/user/dfadeyev/dfadeyev/part-m-00000 524288000 bytes, 4 block(s):  OK
0. BP-373098506-172.31.112.254-1497909673887:blk_1073743829_3005 len=134217728 Live_repl=3
1. BP-373098506-172.31.112.254-1497909673887:blk_1073743830_3006 len=134217728 Live_repl=3
2. BP-373098506-172.31.112.254-1497909673887:blk_1073743831_3007 len=134217728 Live_repl=3
3. BP-373098506-172.31.112.254-1497909673887:blk_1073743832_3008 len=121634816 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	0
 Total files:	1
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue Jun 20 11:23:22 PDT 2017 in 1 milliseconds
```
The source file and targe file is the same!




