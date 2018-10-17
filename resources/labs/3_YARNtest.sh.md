#!/bin/sh
# Confirm the path values given below correspond to your installation

MR=/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce
HADOOP=/opt/cloudera/parcels/CDH/bin

# Mark start of the loop
echo Testing loop started on `date`

# Mapper containers
for i in 4 8 
do
   # Reducer containers
   for j in 2 4
   do                 
      # Container memory
      for k in 512 1024
      do                         
         # Set mapper JVM heap 
         MAP_MB=`echo "($k*0.8)/1" | bc` 

         # Set reducer JVM heap 
         RED_MB=`echo "($k*0.8)/1" | bc` 

        echo '----------- New Test -----------'
        echo '#Mapper/s = ' $i
        echo '#Reducer/s = ' $j
        echo 'Memory = ' $k

        echo -e '\n'
        echo 'Starting Teragen'
        time sudo -u hdfs ${HADOOP}/hadoop jar ${MR}/hadoop-examples.jar teragen \
                     -Dmapreduce.job.maps=$i \
                     -Dmapreduce.map.memory.mb=$k \
                     -Ddfs.replication=1 \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     107374182 /results/tg-10GB-${i}-${j}-${k} 1>tera_${i}_${j}_${k}.out 2>tera_${i}_${j}_${k}.err     

        echo -e '\n'
        echo 'Starting Terasort'
        time sudo -u hdfs ${HADOOP}/hadoop jar $MR/hadoop-examples.jar terasort \
                     -Dmapreduce.job.maps=$i \  
                     -Dmapreduce.job.reduces=$j \
                     -Dmapreduce.map.memory.mb=$k \
                     -Dmapreduce.map.java.opts.max.heap=$MAP_MB \
                     -Dmapreduce.reduce.memory.mb=$k \
                     -Dmapreduce.reduce.java.opts.max.heap=$RED_MB \
               /results/tg-10GB-${i}-${j}-${k}  \
                     /results/ts-10GB-${i}-${j}-${k} 1>>tera_${i}_${j}_${k}.out 2>>tera_${i}_${j}_${k}.err                         

        sudo -u hdfs $HADOOP/hadoop fs -rm -r -skipTrash /results/tg-10GB-${i}-${j}-${k}                         
        sudo -u hdfs $HADOOP/hadoop fs -rm -r -skipTrash /results/ts-10GB-${i}-${j}-${k}                 

        echo '----------- End Test -----------'
      done
   done
done

echo Testing loop ended on `date`
