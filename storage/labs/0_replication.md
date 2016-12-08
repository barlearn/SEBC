I could not establish replication with other participants , so hence i have done a local replication as below

I am attaching a screen shot of my attempt to replicate and also the job in BDR

[barlearn@ip-172-31-10-176 ~]$ hdfs dfs  -ls
Found 5 items
drwx------   - barlearn barlearn          0 2016-12-08 09:38 .Trash
drwx------   - barlearn barlearn          0 2016-12-08 09:56 .staging
drwxr-xr-x   - barlearn barlearn          0 2016-12-08 09:56 test
drwxr-xr-x   - barlearn barlearn          0 2016-12-08 09:35 test1
drwxr-xr-x   - hdfs     barlearn          0 2016-12-08 09:53 test2
[barlearn@ip-172-31-10-176 ~]$ hdfs dfs  -du -s -h test
95.4 M  286.1 M  test
[barlearn@ip-172-31-10-176 ~]$ hdfs dfs  -du -s -h test2
95.4 M  286.1 M  test2
[barlearn@ip-172-31-10-176 ~]$
