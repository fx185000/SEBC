#1.The full teragen command and output
```
[saturn@fx185000-1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapreduce.map.memory.mb=512 -Dmapred.map.tasks=12 -Ddfs.block.size=33554432 65536000 /user/saturn/tgen
17/06/23 11:11:41 INFO client.RMProxy: Connecting to ResourceManager at fx185000-1.vpc.cloudera.com/172.28.199.152:8032
17/06/23 11:11:41 INFO terasort.TeraSort: Generating 65536000 using 12
17/06/23 11:11:41 INFO mapreduce.JobSubmitter: number of splits:12
17/06/23 11:11:41 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/06/23 11:11:41 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/06/23 11:11:41 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1498240347277_0001
17/06/23 11:11:42 INFO impl.YarnClientImpl: Submitted application application_1498240347277_0001
17/06/23 11:11:42 INFO mapreduce.Job: The url to track the job: http://fx185000-1.vpc.cloudera.com:8088/proxy/application_1498240347277_0001/
17/06/23 11:11:42 INFO mapreduce.Job: Running job: job_1498240347277_0001
17/06/23 11:11:49 INFO mapreduce.Job: Job job_1498240347277_0001 running in uber mode : false
17/06/23 11:11:49 INFO mapreduce.Job:  map 0% reduce 0%
17/06/23 11:12:02 INFO mapreduce.Job:  map 6% reduce 0%
17/06/23 11:12:05 INFO mapreduce.Job:  map 17% reduce 0%
17/06/23 11:12:09 INFO mapreduce.Job:  map 28% reduce 0%
17/06/23 11:12:10 INFO mapreduce.Job:  map 29% reduce 0%
17/06/23 11:12:12 INFO mapreduce.Job:  map 38% reduce 0%
17/06/23 11:12:13 INFO mapreduce.Job:  map 39% reduce 0%
17/06/23 11:12:14 INFO mapreduce.Job:  map 40% reduce 0%
17/06/23 11:12:15 INFO mapreduce.Job:  map 49% reduce 0%
17/06/23 11:12:16 INFO mapreduce.Job:  map 51% reduce 0%
17/06/23 11:12:18 INFO mapreduce.Job:  map 59% reduce 0%
17/06/23 11:12:19 INFO mapreduce.Job:  map 61% reduce 0%
17/06/23 11:12:21 INFO mapreduce.Job:  map 68% reduce 0%
17/06/23 11:12:22 INFO mapreduce.Job:  map 69% reduce 0%
17/06/23 11:12:23 INFO mapreduce.Job:  map 71% reduce 0%
17/06/23 11:12:24 INFO mapreduce.Job:  map 75% reduce 0%
17/06/23 11:12:25 INFO mapreduce.Job:  map 77% reduce 0%
17/06/23 11:12:26 INFO mapreduce.Job:  map 79% reduce 0%
17/06/23 11:12:27 INFO mapreduce.Job:  map 84% reduce 0%
17/06/23 11:12:28 INFO mapreduce.Job:  map 86% reduce 0%
17/06/23 11:12:29 INFO mapreduce.Job:  map 89% reduce 0%
17/06/23 11:12:30 INFO mapreduce.Job:  map 92% reduce 0%
17/06/23 11:12:31 INFO mapreduce.Job:  map 94% reduce 0%
17/06/23 11:12:32 INFO mapreduce.Job:  map 95% reduce 0%
17/06/23 11:12:33 INFO mapreduce.Job:  map 99% reduce 0%
17/06/23 11:12:34 INFO mapreduce.Job:  map 100% reduce 0%
17/06/23 11:12:34 INFO mapreduce.Job: Job job_1498240347277_0001 completed successfully
17/06/23 11:12:34 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=1473143
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=1025
		HDFS: Number of bytes written=6553600000
		HDFS: Number of read operations=48
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=24
	Job Counters
		Launched map tasks=12
		Other local map tasks=12
		Total time spent by all maps in occupied slots (ms)=439062
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=439062
		Total vcore-seconds taken by all map tasks=439062
		Total megabyte-seconds taken by all map tasks=449599488
	Map-Reduce Framework
		Map input records=65536000
		Map output records=65536000
		Input split bytes=1025
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=3166
		CPU time spent (ms)=163940
		Physical memory (bytes) snapshot=2455789568
		Virtual memory (bytes) snapshot=13421002752
		Total committed heap usage (bytes)=3036151808
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=140750829423462787
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=6553600000
```

#2.The result of the time command
```
real	0m56.592s
user	0m6.395s
sys	0m0.624s
```
#3.The command and output of hdfs dfs -ls /user/saturn/tgen
```
[saturn@fx185000-1 ~]$ hdfs dfs -ls /user/saturn/tgen
Found 13 items
-rw-r--r--   3 saturn planets          0 2017-06-23 11:12 /user/saturn/tgen/_SUCCESS
-rw-r--r--   3 saturn planets  546133400 2017-06-23 11:12 /user/saturn/tgen/part-m-00000
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00001
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00002
-rw-r--r--   3 saturn planets  546133400 2017-06-23 11:12 /user/saturn/tgen/part-m-00003
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00004
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00005
-rw-r--r--   3 saturn planets  546133400 2017-06-23 11:12 /user/saturn/tgen/part-m-00006
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00007
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00008
-rw-r--r--   3 saturn planets  546133400 2017-06-23 11:12 /user/saturn/tgen/part-m-00009
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00010
-rw-r--r--   3 saturn planets  546133300 2017-06-23 11:12 /user/saturn/tgen/part-m-00011
```
#4.The command and output of hadoop fsck -blocks /user/saturn
```
[saturn@fx185000-1 ~]$ hadoop fsck -blocks /user/saturn
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://fx185000-1.vpc.cloudera.com:50070
FSCK started by saturn (auth:SIMPLE) from /172.28.199.152 for path /user/saturn at Fri Jun 23 11:13:23 PDT 2017
.............Status: HEALTHY
 Total size:	6553600000 B
 Total dirs:	3
 Total files:	13
 Total symlinks:		0
 Total blocks (validated):	204 (avg. block size 32125490 B)
 Minimally replicated blocks:	204 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		4
 Number of racks:		1
FSCK ended at Fri Jun 23 11:13:23 PDT 2017 in 12 milliseconds


The filesystem under path '/user/saturn' is HEALTHY
```