#!/bin/bash
# Confirm the path values given below correspond to your installation

HADOOP_MR="/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce"
HADOOP_PATH="/opt/cloudera/parcels/CDH/bin"

# Mark start of the loop
echo "Testing loop started on" `date`

# Mapper containers
for i in  2
do
# Reducer containers
   for j in 1
   do
      # Container memory
      for k in 512 1024
      do
         # Set mapper JVM heap
         MAP_MB=`echo "($k*0.8)/1" | bc`
         # Set reducer JVM heap
         RED_MB=`echo "($k*0.8)/1" | bc`


    START=`date +%s`;

        $HADOOP_PATH/hadoop jar $HADOOP_MR/hadoop-examples.jar teragen \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     100000 /user/barlearn/tg-10GB-${i}-${j}-${k} 1>tera_${i}_${j}_${k}.out 2>tera_${i}_${j}_${k}.err

    END=`date +%s`
    RUNTIME=$((END-START))

    echo " $HADOOP_PATH/hadoop jar $HADOOP_MR/hadoop-examples.jar teragen  -Dmapreduce.job.maps=$i -Dmapreduce.map.memory.mb=$k -Dmapreduce.map.java.opts.max.heap=$MAP_MB 100000 /user/barlearn/tg-10GB-${i}-${j}-${k} elapsed: $RUNTIME"

    START=`date +%s`;
        $HADOOP_PATH/hadoop jar $HADOOP_MR/hadoop-examples.jar terasort \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.job.reduces=$j \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     -Dmapreduce.reduce.memory.mb=$k \
                     -Dmapreduce.reduce.java.opts.max.heap=$RED_MB \
                 /user/barlearn/tg-10GB-${i}-${j}-${k}  \
                     /user/barlearn/ts-10GB-${i}-${j}-${k} 1>>tera_${i}_${j}_${k}.out 2>>tera_${i}_${j}_${k}.err

    END=`date +%s`
    RUNTIME=$((END-START))

    echo "$HADOOP_PATH/hadoop jar $HADOOP_MR/hadoop-examples.jar terasort -Dmapreduce.job.maps=$i -Dmapreduce.job.reduces=$j -Dmapreduce.map.memory.mb=$k -Dmapreduce.map.java.opts.max.heap=$MAP_MB -Dmapreduce.reduce.memory.mb=$k /user/barlearn/tg-10GB-${i}-${j}-${k} -Dmapreduce.reduce.java.opts.max.heap=$RED_MB elapsed: $RUNTIME"

        $HADOOP_PATH/hadoop fs -rm -r -skipTrash /user/barlearn/tg-10GB-${i}-${j}-${k}
        $HADOOP_PATH/hadoop fs -rm -r -skipTrash /user/barlearn/ts-10GB-${i}-${j}-${k}
      done
   done
done

echo Testing loop ended on `date`
