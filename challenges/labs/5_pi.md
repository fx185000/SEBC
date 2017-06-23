```
[haley@fx185000-1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 10
Number of Maps  = 10
Samples per Map = 10
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/06/23 12:00:05 INFO client.RMProxy: Connecting to ResourceManager at fx185000-1.vpc.cloudera.com/172.28.199.152:8032
17/06/23 12:00:06 INFO hdfs.DFSClient: Created token for haley: HDFS_DELEGATION_TOKEN owner=haley@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244406103, maxDate=1498849206103, sequenceNumber=11, masterKeyId=2 on 172.28.199.152:8020
17/06/23 12:00:06 INFO security.TokenCache: Got dt for hdfs://fx185000-1.vpc.cloudera.com:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.28.199.152:8020, Ident: (token for haley: HDFS_DELEGATION_TOKEN owner=haley@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244406103, maxDate=1498849206103, sequenceNumber=11, masterKeyId=2)
17/06/23 12:00:06 INFO input.FileInputFormat: Total input paths to process : 10
17/06/23 12:00:06 INFO mapreduce.JobSubmitter: number of splits:10
17/06/23 12:00:06 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1498244174765_0003
17/06/23 12:00:06 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.28.199.152:8020, Ident: (token for haley: HDFS_DELEGATION_TOKEN owner=haley@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244406103, maxDate=1498849206103, sequenceNumber=11, masterKeyId=2)
17/06/23 12:00:07 INFO impl.YarnClientImpl: Submitted application application_1498244174765_0003
17/06/23 12:00:07 INFO mapreduce.Job: The url to track the job: http://fx185000-1.vpc.cloudera.com:8088/proxy/application_1498244174765_0003/
17/06/23 12:00:07 INFO mapreduce.Job: Running job: job_1498244174765_0003
17/06/23 12:00:16 INFO mapreduce.Job: Job job_1498244174765_0003 running in uber mode : false
17/06/23 12:00:16 INFO mapreduce.Job:  map 0% reduce 0%
17/06/23 12:00:24 INFO mapreduce.Job:  map 20% reduce 0%
17/06/23 12:00:27 INFO mapreduce.Job:  map 40% reduce 0%
17/06/23 12:00:30 INFO mapreduce.Job:  map 80% reduce 0%
17/06/23 12:00:31 INFO mapreduce.Job:  map 100% reduce 0%
17/06/23 12:00:37 INFO mapreduce.Job:  map 100% reduce 100%
17/06/23 12:00:37 INFO mapreduce.Job: Job job_1498244174765_0003 completed successfully
17/06/23 12:00:37 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=90
		FILE: Number of bytes written=1366345
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=2820
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=43
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters
		Launched map tasks=10
		Launched reduce tasks=1
		Data-local map tasks=9
		Rack-local map tasks=1
		Total time spent by all maps in occupied slots (ms)=101579
		Total time spent by all reduces in occupied slots (ms)=4105
		Total time spent by all map tasks (ms)=101579
		Total time spent by all reduce tasks (ms)=4105
		Total vcore-seconds taken by all map tasks=101579
		Total vcore-seconds taken by all reduce tasks=4105
		Total megabyte-seconds taken by all map tasks=104016896
		Total megabyte-seconds taken by all reduce tasks=4203520
	Map-Reduce Framework
		Map input records=10
		Map output records=20
		Map output bytes=180
		Map output materialized bytes=339
		Input split bytes=1640
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=339
		Reduce input records=20
		Reduce output records=0
		Spilled Records=40
		Shuffled Maps =10
		Failed Shuffles=0
		Merged Map outputs=10
		GC time elapsed (ms)=451
		CPU time spent (ms)=9230
		Physical memory (bytes) snapshot=4741341184
		Virtual memory (bytes) snapshot=17202135040
		Total committed heap usage (bytes)=5507121152
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=1180
	File Output Format Counters
		Bytes Written=97
Job Finished in 31.834 seconds
Estimated value of Pi is 3.20000000000000000000

real	0m35.246s
user	0m5.970s
sys	0m0.649s
```