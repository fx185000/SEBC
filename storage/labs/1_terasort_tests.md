#1.Create an end-user Linux account named with your GitHub handle
```
Fengs-MacPro:~ feng.xu$ ./runall.sh "useradd fx185000"
commandline: ssh root@feng-xu-1.vpc.cloudera.com useradd fx185000 ...
commandline: ssh root@feng-xu-2.vpc.cloudera.com useradd fx185000 ...
commandline: ssh root@feng-xu-3.vpc.cloudera.com useradd fx185000 ...
commandline: ssh root@feng-xu-4.vpc.cloudera.com useradd fx185000 ...
commandline: ssh root@feng-xu-5.vpc.cloudera.com useradd fx185000 ...

[hdfs@feng-xu-1 ~]$ hdfs dfs -mkdir /user/fx185000
[hdfs@feng-xu-1 ~]$ hdfs dfs -chown fx185000:fx185000 /user/fx185000
```

#2.reate a 10 GB file using teragen
```
[fx185000@feng-xu-1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar teragen -Dmapred.map.tasks=4 -D dfs.blocksize=33554432 107374180 /user/fx185000/file10GB
17/06/20 11:52:11 INFO client.RMProxy: Connecting to ResourceManager at feng-xu-1.vpc.cloudera.com/172.28.210.128:8032
17/06/20 11:52:12 INFO terasort.TeraSort: Generating 107374180 using 4
17/06/20 11:52:12 INFO mapreduce.JobSubmitter: number of splits:4
17/06/20 11:52:12 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/06/20 11:52:12 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1497920647653_0005
17/06/20 11:52:13 INFO impl.YarnClientImpl: Submitted application application_1497920647653_0005
17/06/20 11:52:13 INFO mapreduce.Job: The url to track the job: http://feng-xu-1.vpc.cloudera.com:8088/proxy/application_1497920647653_0005/
17/06/20 11:52:13 INFO mapreduce.Job: Running job: job_1497920647653_0005
17/06/20 11:52:18 INFO mapreduce.Job: Job job_1497920647653_0005 running in uber mode : false
17/06/20 11:52:18 INFO mapreduce.Job:  map 0% reduce 0%
17/06/20 11:52:29 INFO mapreduce.Job:  map 5% reduce 0%
17/06/20 11:52:32 INFO mapreduce.Job:  map 12% reduce 0%
17/06/20 11:52:35 INFO mapreduce.Job:  map 17% reduce 0%
17/06/20 11:52:38 INFO mapreduce.Job:  map 20% reduce 0%
17/06/20 11:52:41 INFO mapreduce.Job:  map 23% reduce 0%
17/06/20 11:52:44 INFO mapreduce.Job:  map 27% reduce 0%
17/06/20 11:52:47 INFO mapreduce.Job:  map 29% reduce 0%
17/06/20 11:52:50 INFO mapreduce.Job:  map 33% reduce 0%
17/06/20 11:52:53 INFO mapreduce.Job:  map 36% reduce 0%
17/06/20 11:52:56 INFO mapreduce.Job:  map 39% reduce 0%
17/06/20 11:52:59 INFO mapreduce.Job:  map 42% reduce 0%
17/06/20 11:53:02 INFO mapreduce.Job:  map 46% reduce 0%
17/06/20 11:53:05 INFO mapreduce.Job:  map 49% reduce 0%
17/06/20 11:53:08 INFO mapreduce.Job:  map 52% reduce 0%
17/06/20 11:53:11 INFO mapreduce.Job:  map 56% reduce 0%
17/06/20 11:53:14 INFO mapreduce.Job:  map 59% reduce 0%
17/06/20 11:53:17 INFO mapreduce.Job:  map 62% reduce 0%
17/06/20 11:53:20 INFO mapreduce.Job:  map 65% reduce 0%
17/06/20 11:53:23 INFO mapreduce.Job:  map 68% reduce 0%
17/06/20 11:53:26 INFO mapreduce.Job:  map 72% reduce 0%
17/06/20 11:53:27 INFO mapreduce.Job:  map 73% reduce 0%
17/06/20 11:53:29 INFO mapreduce.Job:  map 75% reduce 0%
17/06/20 11:53:32 INFO mapreduce.Job:  map 78% reduce 0%
17/06/20 11:53:35 INFO mapreduce.Job:  map 80% reduce 0%
17/06/20 11:53:38 INFO mapreduce.Job:  map 83% reduce 0%
17/06/20 11:53:41 INFO mapreduce.Job:  map 86% reduce 0%
17/06/20 11:53:44 INFO mapreduce.Job:  map 88% reduce 0%
17/06/20 11:53:47 INFO mapreduce.Job:  map 91% reduce 0%
17/06/20 11:53:50 INFO mapreduce.Job:  map 93% reduce 0%
17/06/20 11:53:53 INFO mapreduce.Job:  map 96% reduce 0%
17/06/20 11:53:56 INFO mapreduce.Job:  map 99% reduce 0%
17/06/20 11:53:58 INFO mapreduce.Job:  map 100% reduce 0%
17/06/20 11:53:59 INFO mapreduce.Job: Job job_1497920647653_0005 completed successfully
17/06/20 11:53:59 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=490616
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10737418000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=361477
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=361477
		Total vcore-seconds taken by all map tasks=361477
		Total megabyte-seconds taken by all map tasks=370152448
	Map-Reduce Framework
		Map input records=107374180
		Map output records=107374180
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1744
		CPU time spent (ms)=164600
		Physical memory (bytes) snapshot=844877824
		Virtual memory (bytes) snapshot=6277439488
		Total committed heap usage (bytes)=942145536
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=230593858507236407
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10737418000

real	1m50.477s
user	0m5.896s
sys	0m0.253s

[fx185000@feng-xu-1 ~]$ hdfs dfs -ls /user/fx185000/file10GB
Found 5 items
-rw-r--r--   3 fx185000 fx185000          0 2017-06-20 11:53 /user/fx185000/file10GB/_SUCCESS
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00000
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00001
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00002
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00003

```

#3.Run the terasort command on this file

```
[fx185000@feng-xu-1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-examples.jar terasort -Dmapred.reduce.tasks=8 /user/fx185000/file10GB /user/fx185000/file10GBSort
17/06/20 12:02:19 INFO terasort.TeraSort: starting
17/06/20 12:02:20 INFO input.FileInputFormat: Total input paths to process : 4
Spent 285ms computing base-splits.
Spent 6ms computing TeraScheduler splits.
Computing input splits took 292ms
Sampling 10 splits of 320
Making 8 from 100000 sampled records
Computing parititions took 824ms
Spent 1119ms computing partitions.
17/06/20 12:02:21 INFO client.RMProxy: Connecting to ResourceManager at feng-xu-1.vpc.cloudera.com/172.28.210.128:8032
17/06/20 12:02:22 INFO mapreduce.JobSubmitter: number of splits:320
17/06/20 12:02:22 INFO Configuration.deprecation: mapred.reduce.tasks is deprecated. Instead, use mapreduce.job.reduces
17/06/20 12:02:22 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1497920647653_0006
17/06/20 12:02:22 INFO impl.YarnClientImpl: Submitted application application_1497920647653_0006
17/06/20 12:02:22 INFO mapreduce.Job: The url to track the job: http://feng-xu-1.vpc.cloudera.com:8088/proxy/application_1497920647653_0006/
17/06/20 12:02:22 INFO mapreduce.Job: Running job: job_1497920647653_0006
17/06/20 12:02:27 INFO mapreduce.Job: Job job_1497920647653_0006 running in uber mode : false
17/06/20 12:02:27 INFO mapreduce.Job:  map 0% reduce 0%
17/06/20 12:02:38 INFO mapreduce.Job:  map 1% reduce 0%
17/06/20 12:02:39 INFO mapreduce.Job:  map 2% reduce 0%
17/06/20 12:02:40 INFO mapreduce.Job:  map 3% reduce 0%
17/06/20 12:02:41 INFO mapreduce.Job:  map 4% reduce 0%
17/06/20 12:02:42 INFO mapreduce.Job:  map 5% reduce 0%
17/06/20 12:02:47 INFO mapreduce.Job:  map 6% reduce 0%
17/06/20 12:02:51 INFO mapreduce.Job:  map 8% reduce 0%
17/06/20 12:02:56 INFO mapreduce.Job:  map 10% reduce 0%
17/06/20 12:03:02 INFO mapreduce.Job:  map 11% reduce 0%
17/06/20 12:03:04 INFO mapreduce.Job:  map 13% reduce 0%
17/06/20 12:03:07 INFO mapreduce.Job:  map 14% reduce 0%
17/06/20 12:03:09 INFO mapreduce.Job:  map 15% reduce 0%
17/06/20 12:03:13 INFO mapreduce.Job:  map 16% reduce 0%
17/06/20 12:03:15 INFO mapreduce.Job:  map 18% reduce 0%
17/06/20 12:03:20 INFO mapreduce.Job:  map 19% reduce 0%
17/06/20 12:03:22 INFO mapreduce.Job:  map 20% reduce 0%
17/06/20 12:03:24 INFO mapreduce.Job:  map 21% reduce 0%
17/06/20 12:03:26 INFO mapreduce.Job:  map 22% reduce 0%
17/06/20 12:03:27 INFO mapreduce.Job:  map 23% reduce 0%
17/06/20 12:03:32 INFO mapreduce.Job:  map 24% reduce 0%
17/06/20 12:03:34 INFO mapreduce.Job:  map 25% reduce 0%
17/06/20 12:03:35 INFO mapreduce.Job:  map 26% reduce 0%
17/06/20 12:03:37 INFO mapreduce.Job:  map 27% reduce 0%
17/06/20 12:03:38 INFO mapreduce.Job:  map 28% reduce 0%
17/06/20 12:03:42 INFO mapreduce.Job:  map 29% reduce 0%
17/06/20 12:03:47 INFO mapreduce.Job:  map 30% reduce 0%
17/06/20 12:03:48 INFO mapreduce.Job:  map 32% reduce 0%
17/06/20 12:03:50 INFO mapreduce.Job:  map 33% reduce 0%
17/06/20 12:03:56 INFO mapreduce.Job:  map 34% reduce 0%
17/06/20 12:03:59 INFO mapreduce.Job:  map 36% reduce 0%
17/06/20 12:04:00 INFO mapreduce.Job:  map 38% reduce 0%
17/06/20 12:04:07 INFO mapreduce.Job:  map 39% reduce 0%
17/06/20 12:04:09 INFO mapreduce.Job:  map 40% reduce 0%
17/06/20 12:04:10 INFO mapreduce.Job:  map 41% reduce 0%
17/06/20 12:04:12 INFO mapreduce.Job:  map 42% reduce 0%
17/06/20 12:04:14 INFO mapreduce.Job:  map 43% reduce 0%
17/06/20 12:04:17 INFO mapreduce.Job:  map 44% reduce 0%
17/06/20 12:04:20 INFO mapreduce.Job:  map 45% reduce 0%
17/06/20 12:04:22 INFO mapreduce.Job:  map 46% reduce 0%
17/06/20 12:04:24 INFO mapreduce.Job:  map 47% reduce 0%
17/06/20 12:04:26 INFO mapreduce.Job:  map 48% reduce 0%
17/06/20 12:04:29 INFO mapreduce.Job:  map 49% reduce 0%
17/06/20 12:04:31 INFO mapreduce.Job:  map 50% reduce 0%
17/06/20 12:04:33 INFO mapreduce.Job:  map 51% reduce 0%
17/06/20 12:04:35 INFO mapreduce.Job:  map 52% reduce 0%
17/06/20 12:04:39 INFO mapreduce.Job:  map 53% reduce 0%
17/06/20 12:04:42 INFO mapreduce.Job:  map 55% reduce 0%
17/06/20 12:04:44 INFO mapreduce.Job:  map 56% reduce 0%
17/06/20 12:04:45 INFO mapreduce.Job:  map 57% reduce 0%
17/06/20 12:04:51 INFO mapreduce.Job:  map 58% reduce 0%
17/06/20 12:04:53 INFO mapreduce.Job:  map 60% reduce 0%
17/06/20 12:04:55 INFO mapreduce.Job:  map 61% reduce 0%
17/06/20 12:04:59 INFO mapreduce.Job:  map 62% reduce 0%
17/06/20 12:05:02 INFO mapreduce.Job:  map 63% reduce 0%
17/06/20 12:05:05 INFO mapreduce.Job:  map 65% reduce 0%
17/06/20 12:05:06 INFO mapreduce.Job:  map 66% reduce 0%
17/06/20 12:05:09 INFO mapreduce.Job:  map 67% reduce 0%
17/06/20 12:05:16 INFO mapreduce.Job:  map 69% reduce 0%
17/06/20 12:05:17 INFO mapreduce.Job:  map 70% reduce 0%
17/06/20 12:05:18 INFO mapreduce.Job:  map 71% reduce 0%
17/06/20 12:05:19 INFO mapreduce.Job:  map 72% reduce 0%
17/06/20 12:05:27 INFO mapreduce.Job:  map 74% reduce 0%
17/06/20 12:05:28 INFO mapreduce.Job:  map 75% reduce 0%
17/06/20 12:05:30 INFO mapreduce.Job:  map 76% reduce 0%
17/06/20 12:05:31 INFO mapreduce.Job:  map 77% reduce 0%
17/06/20 12:05:38 INFO mapreduce.Job:  map 78% reduce 0%
17/06/20 12:05:41 INFO mapreduce.Job:  map 80% reduce 0%
17/06/20 12:05:43 INFO mapreduce.Job:  map 81% reduce 0%
17/06/20 12:05:45 INFO mapreduce.Job:  map 82% reduce 0%
17/06/20 12:05:50 INFO mapreduce.Job:  map 83% reduce 0%
17/06/20 12:05:52 INFO mapreduce.Job:  map 84% reduce 0%
17/06/20 12:05:53 INFO mapreduce.Job:  map 85% reduce 0%
17/06/20 12:05:56 INFO mapreduce.Job:  map 85% reduce 2%
17/06/20 12:05:57 INFO mapreduce.Job:  map 85% reduce 3%
17/06/20 12:05:58 INFO mapreduce.Job:  map 85% reduce 5%
17/06/20 12:05:59 INFO mapreduce.Job:  map 85% reduce 8%
17/06/20 12:06:00 INFO mapreduce.Job:  map 85% reduce 9%
17/06/20 12:06:01 INFO mapreduce.Job:  map 86% reduce 9%
17/06/20 12:06:02 INFO mapreduce.Job:  map 86% reduce 12%
17/06/20 12:06:03 INFO mapreduce.Job:  map 86% reduce 13%
17/06/20 12:06:06 INFO mapreduce.Job:  map 88% reduce 17%
17/06/20 12:06:07 INFO mapreduce.Job:  map 88% reduce 18%
17/06/20 12:06:09 INFO mapreduce.Job:  map 88% reduce 19%
17/06/20 12:06:10 INFO mapreduce.Job:  map 88% reduce 20%
17/06/20 12:06:11 INFO mapreduce.Job:  map 88% reduce 21%
17/06/20 12:06:12 INFO mapreduce.Job:  map 88% reduce 23%
17/06/20 12:06:15 INFO mapreduce.Job:  map 89% reduce 24%
17/06/20 12:06:16 INFO mapreduce.Job:  map 89% reduce 26%
17/06/20 12:06:17 INFO mapreduce.Job:  map 90% reduce 26%
17/06/20 12:06:18 INFO mapreduce.Job:  map 91% reduce 26%
17/06/20 12:06:23 INFO mapreduce.Job:  map 92% reduce 26%
17/06/20 12:06:24 INFO mapreduce.Job:  map 92% reduce 27%
17/06/20 12:06:29 INFO mapreduce.Job:  map 93% reduce 27%
17/06/20 12:06:30 INFO mapreduce.Job:  map 94% reduce 27%
17/06/20 12:06:33 INFO mapreduce.Job:  map 95% reduce 27%
17/06/20 12:06:34 INFO mapreduce.Job:  map 95% reduce 28%
17/06/20 12:06:37 INFO mapreduce.Job:  map 96% reduce 28%
17/06/20 12:06:42 INFO mapreduce.Job:  map 98% reduce 28%
17/06/20 12:06:45 INFO mapreduce.Job:  map 98% reduce 29%
17/06/20 12:06:48 INFO mapreduce.Job:  map 99% reduce 29%
17/06/20 12:06:53 INFO mapreduce.Job:  map 100% reduce 29%
17/06/20 12:06:54 INFO mapreduce.Job:  map 100% reduce 32%
17/06/20 12:06:55 INFO mapreduce.Job:  map 100% reduce 37%
17/06/20 12:06:56 INFO mapreduce.Job:  map 100% reduce 39%
17/06/20 12:06:57 INFO mapreduce.Job:  map 100% reduce 46%
17/06/20 12:06:58 INFO mapreduce.Job:  map 100% reduce 59%
17/06/20 12:06:59 INFO mapreduce.Job:  map 100% reduce 61%
17/06/20 12:07:00 INFO mapreduce.Job:  map 100% reduce 62%
17/06/20 12:07:01 INFO mapreduce.Job:  map 100% reduce 65%
17/06/20 12:07:03 INFO mapreduce.Job:  map 100% reduce 66%
17/06/20 12:07:04 INFO mapreduce.Job:  map 100% reduce 70%
17/06/20 12:07:06 INFO mapreduce.Job:  map 100% reduce 71%
17/06/20 12:07:07 INFO mapreduce.Job:  map 100% reduce 76%
17/06/20 12:07:08 INFO mapreduce.Job:  map 100% reduce 77%
17/06/20 12:07:09 INFO mapreduce.Job:  map 100% reduce 78%
17/06/20 12:07:10 INFO mapreduce.Job:  map 100% reduce 82%
17/06/20 12:07:12 INFO mapreduce.Job:  map 100% reduce 83%
17/06/20 12:07:13 INFO mapreduce.Job:  map 100% reduce 86%
17/06/20 12:07:15 INFO mapreduce.Job:  map 100% reduce 88%
17/06/20 12:07:16 INFO mapreduce.Job:  map 100% reduce 90%
17/06/20 12:07:17 INFO mapreduce.Job:  map 100% reduce 91%
17/06/20 12:07:18 INFO mapreduce.Job:  map 100% reduce 92%
17/06/20 12:07:19 INFO mapreduce.Job:  map 100% reduce 93%
17/06/20 12:07:20 INFO mapreduce.Job:  map 100% reduce 94%
17/06/20 12:07:21 INFO mapreduce.Job:  map 100% reduce 95%
17/06/20 12:07:22 INFO mapreduce.Job:  map 100% reduce 97%
17/06/20 12:07:25 INFO mapreduce.Job:  map 100% reduce 99%
17/06/20 12:07:27 INFO mapreduce.Job:  map 100% reduce 100%
17/06/20 12:07:27 INFO mapreduce.Job: Job job_1497920647653_0006 completed successfully
17/06/20 12:07:27 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4806399929
		FILE: Number of bytes written=9544717056
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10737462480
		HDFS: Number of bytes written=10737418000
		HDFS: Number of read operations=984
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters 
		Launched map tasks=320
		Launched reduce tasks=8
		Data-local map tasks=320
		Total time spent by all maps in occupied slots (ms)=3104671
		Total time spent by all reduces in occupied slots (ms)=688801
		Total time spent by all map tasks (ms)=3104671
		Total time spent by all reduce tasks (ms)=688801
		Total vcore-seconds taken by all map tasks=3104671
		Total vcore-seconds taken by all reduce tasks=688801
		Total megabyte-seconds taken by all map tasks=3179183104
		Total megabyte-seconds taken by all reduce tasks=705332224
	Map-Reduce Framework
		Map input records=107374180
		Map output records=107374180
		Map output bytes=10952166360
		Map output materialized bytes=4697592957
		Input split bytes=44480
		Combine input records=0
		Combine output records=0
		Reduce input groups=107374180
		Reduce shuffle bytes=4697592957
		Reduce input records=107374180
		Reduce output records=107374180
		Spilled Records=214748360
		Shuffled Maps =2560
		Failed Shuffles=0
		Merged Map outputs=2560
		GC time elapsed (ms)=42093
		CPU time spent (ms)=1529850
		Physical memory (bytes) snapshot=158681440256
		Virtual memory (bytes) snapshot=513525436416
		Total committed heap usage (bytes)=192977305600
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10737418000
	File Output Format Counters 
		Bytes Written=10737418000
17/06/20 12:07:27 INFO terasort.TeraSort: done

real	5m8.958s
user	0m8.421s
sys	0m0.345s

[fx185000@feng-xu-1 ~]$ hdfs dfs -ls /user/fx185000/file10GB
Found 5 items
-rw-r--r--   3 fx185000 fx185000          0 2017-06-20 11:53 /user/fx185000/file10GB/_SUCCESS
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00000
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00001
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00002
-rw-r--r--   3 fx185000 fx185000 2684354500 2017-06-20 11:53 /user/fx185000/file10GB/part-m-00003

[fx185000@feng-xu-1 ~]$ hdfs dfs -ls /user/fx185000/file10GBSort
Found 10 items
-rw-r--r--   1 fx185000 fx185000          0 2017-06-20 12:07 /user/fx185000/file10GBSort/_SUCCESS
-rw-r--r--  10 fx185000 fx185000         77 2017-06-20 12:02 /user/fx185000/file10GBSort/_partition.lst
-rw-r--r--   1 fx185000 fx185000 1341771400 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00000
-rw-r--r--   1 fx185000 fx185000 1321428000 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00001
-rw-r--r--   1 fx185000 fx185000 1344065300 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00002
-rw-r--r--   1 fx185000 fx185000 1351686700 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00003
-rw-r--r--   1 fx185000 fx185000 1349054600 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00004
-rw-r--r--   1 fx185000 fx185000 1362285200 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00005
-rw-r--r--   1 fx185000 fx185000 1323142400 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00006
-rw-r--r--   1 fx185000 fx185000 1343984400 2017-06-20 12:07 /user/fx185000/file10GBSort/part-r-00007

```
