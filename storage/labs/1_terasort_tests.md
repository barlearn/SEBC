#Create a home HDFS directory 

sudo -u hdfs hadoop fs -mkdir /user/root
sudo -u hdfs hadoop fs -chown root:root /user/root

#Directory created for Replication lab
sudo -u hdfs hadoop fs -mkdir /replication

#teragen command
sudo -u hdfs time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen  -Dmapreduce.job.maps=10 5000000 /tmp/tera1_out

#teragen results
[root@ip-172-31-10-176 tmp]# sudo -u hdfs time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen  -Dmapreduce.job.maps=10 5000000 /tmp/tera1_out

16/12/08 05:17:49 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-0-98.ap-southeast-1.compute.internal/172.31.0.98:8032
16/12/08 05:17:50 INFO terasort.TeraSort: Generating 5000000 using 10
16/12/08 05:17:50 INFO mapreduce.JobSubmitter: number of splits:10
16/12/08 05:17:51 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1481157001005_0003
16/12/08 05:17:51 INFO impl.YarnClientImpl: Submitted application application_1481157001005_0003
16/12/08 05:17:51 INFO mapreduce.Job: The url to track the job: http://ip-172-31-0-98.ap-southeast-1.compute.internal:8088/proxy/application_1481157001005_0003/
16/12/08 05:17:51 INFO mapreduce.Job: Running job: job_1481157001005_0003
16/12/08 05:17:59 INFO mapreduce.Job: Job job_1481157001005_0003 running in uber mode : false
16/12/08 05:17:59 INFO mapreduce.Job:  map 0% reduce 0%
16/12/08 05:18:11 INFO mapreduce.Job:  map 10% reduce 0%
16/12/08 05:18:12 INFO mapreduce.Job:  map 30% reduce 0%
16/12/08 05:18:15 INFO mapreduce.Job:  map 40% reduce 0%
16/12/08 05:18:16 INFO mapreduce.Job:  map 100% reduce 0%
16/12/08 05:18:17 INFO mapreduce.Job: Job job_1481157001005_0003 completed successfully
16/12/08 05:18:17 INFO mapreduce.Job: Counters: 31
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=1239690
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=847
                HDFS: Number of bytes written=500000000
                HDFS: Number of read operations=40
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=20
        Job Counters
                Launched map tasks=10
                Other local map tasks=10
                Total time spent by all maps in occupied slots (ms)=130816
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=130816
                Total vcore-seconds taken by all map tasks=130816
                Total megabyte-seconds taken by all map tasks=133955584
        Map-Reduce Framework
                Map input records=5000000
                Map output records=5000000
                Input split bytes=847
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1400
                CPU time spent (ms)=37680
                Physical memory (bytes) snapshot=2422480896
                Virtual memory (bytes) snapshot=15689560064
                Total committed heap usage (bytes)=2951741440
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=10735710707299981
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=500000000

5.49user 
0.69system 
0:30.81elapsed 
20%CPU (0avgtext+0avgdata 224332maxresident)k
0inputs+968outputs (0major+80100minor)pagefaults 
0swaps

#to clear the output file
sudo -u hdfs hadoop fs -rm -r -skipTrash /tmp/tera1_out  
