#create directory

sudo su hdfs
hdfs dfs -mkdir  /user/barlearn
hdfs dfs -chown barlearn:barlearn /user/barlearn

Put data into directory
wget https://github.com/barlearn/SEBC/archive/master.zip
hdfs dfs -put master.zip /user/barlearn
hdfs dfs -ls /user/barlearn

#Enable snapshots

hdfs dfsadmin -allowSnapshot /user/barlearn

#Create snapshots

hdfs dfs -createSnapshot /user/barlear sebc-hdfs-test

#Delete the ZIP file

hdfs dfs -rm /user/barlearn/master.zip

#Restore the deleted file

hdfs dfs -cp  hdfs:///user/barlearn/.snapshot/sebc-hdfs-test/master.zip hdfs:///user/barlearn/.
