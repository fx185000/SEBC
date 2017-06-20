#1.Create a precious directory in HDFS; copy the ZIP course file into it.
```
[fx185000@feng-xu-1 ~]$ hadoop fs -mkdir /user/fx185000/precious
[fx185000@feng-xu-1 ~]$ hadoop fs -copyFromLocal ~/SEBC-master.zip /user/fx185000/precious
```

#2.Enable snapshots for precious
```
[hdfs@feng-xu-1 ~]$ hdfs dfsadmin -allowSnapshot /user/fx185000/precious
Allowing snaphot on /user/fx185000/precious succeeded
```

#3.Create a snapshot called snap1
```
[hdfs@feng-xu-1 ~]$ hdfs dfs -createSnapshot /user/fx185000/precious snap1
Created snapshot /user/fx185000/precious/.snapshot/snap1
```
#4.Delete the ZIP file
```
[hdfs@feng-xu-1 ~]$ hdfs dfs -rm -r /user/fx185000/precious/SEBC-master.zip
17/06/20 13:02:46 INFO fs.TrashPolicyDefault: Moved: 'hdfs://feng-xu-1.vpc.cloudera.com:8020/user/fx185000/precious/SEBC-master.zip' to trash at: hdfs://feng-xu-1.vpc.cloudera.com:8020/user/hdfs/.Trash/Current/user/fx185000/precious/SEBC-master.zip
```

#5.Restore the deleted file
```
[hdfs@feng-xu-1 ~]$ hdfs dfs -ls /user/fx185000/precious/.snapshot/snap1/SEBC-master.zip
-rw-r--r--   3 fx185000 fx185000     474872 2017-06-20 12:57 /user/fx185000/precious/.snapshot/snap1/SEBC-master.zip
[hdfs@feng-xu-1 ~]$ hdfs dfs -cp /user/fx185000/precious/.snapshot/snap1/SEBC-master.zip /user/fx185000/precious/
[hdfs@feng-xu-1 ~]$ hdfs dfs -ls /user/fx185000/precious
Found 1 items
-rw-r--r--   3 hdfs fx185000     474872 2017-06-20 13:07 /user/fx185000/precious/SEBC-master.zip
```
