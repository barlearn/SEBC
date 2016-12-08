Testing loop started on Thu Dec 8 11:05:00 UTC 2016
 /opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen  -Dmapreduce.job.maps=2 -Dmapreduce.map.memory.mb=512 -Dmapreduce.map.java.opts.max.heap=409 100000 /user/barlearn/tg-10GB-2-1-512 elapsed: 20
/opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapreduce.job.maps=2 -Dmapreduce.job.reduces=1 -Dmapreduce.map.memory.mb=512 -Dmapreduce.map.java.opts.max.heap=409 -Dmapreduce.reduce.memory.mb=512 /user/barlearn/tg-10GB-2-1-512 -Dmapreduce.reduce.java.opts.max.heap=409 elapsed: 27
Deleted /user/barlearn/tg-10GB-2-1-512
Deleted /user/barlearn/ts-10GB-2-1-512
 /opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen  -Dmapreduce.job.maps=2 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 100000 /user/barlearn/tg-10GB-2-1-1024 elapsed: 20
/opt/cloudera/parcels/CDH/bin/hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort -Dmapreduce.job.maps=2 -Dmapreduce.job.reduces=1 -Dmapreduce.map.memory.mb=1024 -Dmapreduce.map.java.opts.max.heap=819 -Dmapreduce.reduce.memory.mb=1024 /user/barlearn/tg-10GB-2-1-1024 -Dmapreduce.reduce.java.opts.max.heap=819 elapsed: 29
Deleted /user/barlearn/tg-10GB-2-1-1024
Deleted /user/barlearn/ts-10GB-2-1-1024
Testing loop ended on Thu Dec 8 11:06:46 UTC 2016
