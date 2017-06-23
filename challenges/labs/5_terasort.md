```
[saturn@fx185000-1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen 10000000 /user/saturn/tgen2
17/06/23 11:56:34 INFO client.RMProxy: Connecting to ResourceManager at fx185000-1.vpc.cloudera.com/172.28.199.152:8032
17/06/23 11:56:35 INFO hdfs.DFSClient: Created token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244195065, maxDate=1498848995065, sequenceNumber=9, masterKeyId=2 on 172.28.199.152:8020
17/06/23 11:56:35 INFO security.TokenCache: Got dt for hdfs://fx185000-1.vpc.cloudera.com:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.28.199.152:8020, Ident: (token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244195065, maxDate=1498848995065, sequenceNumber=9, masterKeyId=2)
17/06/23 11:56:35 INFO terasort.TeraSort: Generating 10000000 using 2
17/06/23 11:56:35 INFO mapreduce.JobSubmitter: number of splits:2
17/06/23 11:56:35 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1498244174765_0001
17/06/23 11:56:35 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.28.199.152:8020, Ident: (token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244195065, maxDate=1498848995065, sequenceNumber=9, masterKeyId=2)
17/06/23 11:56:36 INFO impl.YarnClientImpl: Submitted application application_1498244174765_0001
17/06/23 11:56:37 INFO mapreduce.Job: The url to track the job: http://fx185000-1.vpc.cloudera.com:8088/proxy/application_1498244174765_0001/
17/06/23 11:56:37 INFO mapreduce.Job: Running job: job_1498244174765_0001
17/06/23 11:56:48 INFO mapreduce.Job: Job job_1498244174765_0001 running in uber mode : false
17/06/23 11:56:48 INFO mapreduce.Job:  map 0% reduce 0%
17/06/23 11:57:01 INFO mapreduce.Job:  map 49% reduce 0%
17/06/23 11:57:04 INFO mapreduce.Job:  map 83% reduce 0%
17/06/23 11:57:05 INFO mapreduce.Job:  map 100% reduce 0%
17/06/23 11:57:06 INFO mapreduce.Job: Job job_1498244174765_0001 completed successfully
17/06/23 11:57:06 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=247022
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=167
		HDFS: Number of bytes written=1000000000
		HDFS: Number of read operations=8
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=4
	Job Counters
		Launched map tasks=2
		Other local map tasks=2
		Total time spent by all maps in occupied slots (ms)=31102
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=31102
		Total vcore-seconds taken by all map tasks=31102
		Total megabyte-seconds taken by all map tasks=31848448
	Map-Reduce Framework
		Map input records=10000000
		Map output records=10000000
		Input split bytes=167
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=303
		CPU time spent (ms)=24520
		Physical memory (bytes) snapshot=737091584
		Virtual memory (bytes) snapshot=3094233088
		Total committed heap usage (bytes)=793772032
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=21472776955442690
	File Input Format Counters
		Bytes Read=0
	File Output Format Counters
		Bytes Written=1000000000

real	0m34.639s
user	0m6.001s
sys	0m0.613s
[saturn@fx185000-1 ~]$ time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar terasort /user/saturn/tgen2 /user/saturn/tsort
17/06/23 11:57:55 INFO terasort.TeraSort: starting
17/06/23 11:57:56 INFO hdfs.DFSClient: Created token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244276695, maxDate=1498849076695, sequenceNumber=10, masterKeyId=2 on 172.28.199.152:8020
17/06/23 11:57:56 INFO security.TokenCache: Got dt for hdfs://fx185000-1.vpc.cloudera.com:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.28.199.152:8020, Ident: (token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244276695, maxDate=1498849076695, sequenceNumber=10, masterKeyId=2)
17/06/23 11:57:56 INFO input.FileInputFormat: Total input paths to process : 2
Spent 321ms computing base-splits.
Spent 3ms computing TeraScheduler splits.
Computing input splits took 324ms
Sampling 8 splits of 8
Making 8 from 100000 sampled records
Computing parititions took 968ms
Spent 1296ms computing partitions.
17/06/23 11:57:57 INFO client.RMProxy: Connecting to ResourceManager at fx185000-1.vpc.cloudera.com/172.28.199.152:8032
17/06/23 11:57:58 INFO mapreduce.JobSubmitter: number of splits:8
17/06/23 11:57:58 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1498244174765_0002
17/06/23 11:57:58 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.28.199.152:8020, Ident: (token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@FX185000.HQ, renewer=yarn, realUser=, issueDate=1498244276695, maxDate=1498849076695, sequenceNumber=10, masterKeyId=2)
17/06/23 11:57:59 INFO impl.YarnClientImpl: Submitted application application_1498244174765_0002
17/06/23 11:57:59 INFO mapreduce.Job: The url to track the job: http://fx185000-1.vpc.cloudera.com:8088/proxy/application_1498244174765_0002/
17/06/23 11:57:59 INFO mapreduce.Job: Running job: job_1498244174765_0002
17/06/23 11:58:08 INFO mapreduce.Job: Job job_1498244174765_0002 running in uber mode : false
17/06/23 11:58:08 INFO mapreduce.Job:  map 0% reduce 0%
17/06/23 11:58:25 INFO mapreduce.Job:  map 13% reduce 0%
17/06/23 11:58:26 INFO mapreduce.Job:  map 25% reduce 0%
17/06/23 11:58:27 INFO mapreduce.Job:  map 42% reduce 0%
17/06/23 11:58:28 INFO mapreduce.Job:  map 50% reduce 0%
17/06/23 11:58:29 INFO mapreduce.Job:  map 75% reduce 0%
17/06/23 11:58:30 INFO mapreduce.Job:  map 96% reduce 0%
17/06/23 11:58:31 INFO mapreduce.Job:  map 100% reduce 0%
17/06/23 11:58:43 INFO mapreduce.Job:  map 100% reduce 25%
17/06/23 11:58:45 INFO mapreduce.Job:  map 100% reduce 89%
17/06/23 11:58:46 INFO mapreduce.Job:  map 100% reduce 94%
17/06/23 11:58:47 INFO mapreduce.Job:  map 100% reduce 100%
17/06/23 11:58:48 INFO mapreduce.Job: Job job_1498244174765_0002 completed successfully
17/06/23 11:58:49 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=443030807
		FILE: Number of bytes written=885174751
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=1000001080
		HDFS: Number of bytes written=1000000000
		HDFS: Number of read operations=48
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters
		Launched map tasks=8
		Launched reduce tasks=8
		Data-local map tasks=6
		Rack-local map tasks=2
		Total time spent by all maps in occupied slots (ms)=150772
		Total time spent by all reduces in occupied slots (ms)=106074
		Total time spent by all map tasks (ms)=150772
		Total time spent by all reduce tasks (ms)=106074
		Total vcore-seconds taken by all map tasks=150772
		Total vcore-seconds taken by all reduce tasks=106074
		Total megabyte-seconds taken by all map tasks=154390528
		Total megabyte-seconds taken by all reduce tasks=108619776
	Map-Reduce Framework
		Map input records=10000000
		Map output records=10000000
		Map output bytes=1020000000
		Map output materialized bytes=440145104
		Input split bytes=1080
		Combine input records=0
		Combine output records=0
		Reduce input groups=10000000
		Reduce shuffle bytes=440145104
		Reduce input records=10000000
		Reduce output records=10000000
		Spilled Records=20000000
		Shuffled Maps =64
		Failed Shuffles=0
		Merged Map outputs=64
		GC time elapsed (ms)=2669
		CPU time spent (ms)=125350
		Physical memory (bytes) snapshot=7683555328
		Virtual memory (bytes) snapshot=25154273280
		Total committed heap usage (bytes)=8826388480
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters
		Bytes Read=1000000000
	File Output Format Counters
		Bytes Written=1000000000
17/06/23 11:58:49 INFO terasort.TeraSort: done

real	0m55.295s
user	0m8.109s
sys	0m0.722s
```