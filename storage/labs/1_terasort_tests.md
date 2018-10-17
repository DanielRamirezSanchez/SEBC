Create the user

        [daniramirez@sebc-vm2 ~]$ sudo useradd DanielRamirezSanchez
        [daniramirez@sebc-vm2 ~]$ sudo passwd DanielRamirezSanchez

        user DanielRamirezSanchez
        passwd githubuser

The folder /user/DanielRamirezSanchez already exists and has all permissions (777) because of the test done in the previous excercice. That whas the folder I created as my destination for the distcp. I just change de owner.

         sudo -u hdfs hdfs dfs -chown DanielRamirezSanchez /user/DanielRamirezSanchez

Create the 10GB file

        [daniramirez@sebc-vm2 hadoop-mapreduce]$ time sudo -u DanielRamirezSanchez hadoop jar hadoop-mapreduce-examples-2.6.0-cdh5.13.3.jar teragen -Ddfs.block.size=33554432 -Dmapreduce.job.maps=4 100000000 /user/DanielRamirezSanchez/terasort-input10G
        18/10/16 11:55:20 INFO client.RMProxy: Connecting to ResourceManager at sebc-vm2.westeurope.cloudapp.azure.com/10.0.2.6:8032
        18/10/16 11:55:21 INFO terasort.TeraGen: Generating 100000000 using 4
        18/10/16 11:55:26 INFO mapreduce.JobSubmitter: number of splits:4
        18/10/16 11:55:26 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
        18/10/16 11:55:26 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539682780316_0008
        18/10/16 11:55:27 INFO impl.YarnClientImpl: Submitted application application_1539682780316_0008
        18/10/16 11:55:27 INFO mapreduce.Job: The url to track the job: http://sebc-vm2.westeurope.cloudapp.azure.com:8088/proxy/application_1539682780316_0008/
        18/10/16 11:55:27 INFO mapreduce.Job: Running job: job_1539682780316_0008
        18/10/16 11:55:56 INFO mapreduce.Job: Job job_1539682780316_0008 running in uber mode : false
        18/10/16 11:55:56 INFO mapreduce.Job:  map 0% reduce 0%
        18/10/16 11:56:17 INFO mapreduce.Job:  map 8% reduce 0%
        18/10/16 11:56:19 INFO mapreduce.Job:  map 11% reduce 0%
        18/10/16 11:56:20 INFO mapreduce.Job:  map 13% reduce 0%
        18/10/16 11:56:23 INFO mapreduce.Job:  map 16% reduce 0%
        18/10/16 11:56:26 INFO mapreduce.Job:  map 18% reduce 0%
        18/10/16 11:56:30 INFO mapreduce.Job:  map 19% reduce 0%
        18/10/16 11:56:36 INFO mapreduce.Job:  map 20% reduce 0%
        18/10/16 11:56:39 INFO mapreduce.Job:  map 22% reduce 0%
        18/10/16 11:56:42 INFO mapreduce.Job:  map 24% reduce 0%
        18/10/16 11:56:45 INFO mapreduce.Job:  map 25% reduce 0%
        18/10/16 11:56:48 INFO mapreduce.Job:  map 28% reduce 0%
        18/10/16 11:56:51 INFO mapreduce.Job:  map 30% reduce 0%
        18/10/16 11:56:54 INFO mapreduce.Job:  map 33% reduce 0%
        18/10/16 11:56:57 INFO mapreduce.Job:  map 35% reduce 0%
        18/10/16 11:57:00 INFO mapreduce.Job:  map 36% reduce 0%
        18/10/16 11:57:06 INFO mapreduce.Job:  map 38% reduce 0%
        18/10/16 11:57:09 INFO mapreduce.Job:  map 39% reduce 0%
        18/10/16 11:57:12 INFO mapreduce.Job:  map 40% reduce 0%
        18/10/16 11:57:15 INFO mapreduce.Job:  map 41% reduce 0%
        18/10/16 11:57:16 INFO mapreduce.Job:  map 42% reduce 0%
        18/10/16 11:57:18 INFO mapreduce.Job:  map 43% reduce 0%
        18/10/16 11:57:22 INFO mapreduce.Job:  map 44% reduce 0%
        18/10/16 11:57:25 INFO mapreduce.Job:  map 45% reduce 0%
        18/10/16 11:57:27 INFO mapreduce.Job:  map 46% reduce 0%
        18/10/16 11:57:31 INFO mapreduce.Job:  map 47% reduce 0%
        18/10/16 11:57:37 INFO mapreduce.Job:  map 49% reduce 0%
        18/10/16 11:57:41 INFO mapreduce.Job:  map 50% reduce 0%
        18/10/16 11:57:43 INFO mapreduce.Job:  map 51% reduce 0%
        18/10/16 11:57:45 INFO mapreduce.Job:  map 52% reduce 0%
        18/10/16 11:57:47 INFO mapreduce.Job:  map 53% reduce 0%
        18/10/16 11:57:49 INFO mapreduce.Job:  map 54% reduce 0%
        18/10/16 11:57:53 INFO mapreduce.Job:  map 55% reduce 0%
        18/10/16 11:57:55 INFO mapreduce.Job:  map 56% reduce 0%
        18/10/16 11:57:57 INFO mapreduce.Job:  map 57% reduce 0%
        18/10/16 11:58:01 INFO mapreduce.Job:  map 59% reduce 0%
        18/10/16 11:58:07 INFO mapreduce.Job:  map 61% reduce 0%
        18/10/16 11:58:11 INFO mapreduce.Job:  map 62% reduce 0%
        18/10/16 11:58:13 INFO mapreduce.Job:  map 63% reduce 0%
        18/10/16 11:58:15 INFO mapreduce.Job:  map 64% reduce 0%
        18/10/16 11:58:19 INFO mapreduce.Job:  map 65% reduce 0%
        18/10/16 11:58:21 INFO mapreduce.Job:  map 66% reduce 0%
        18/10/16 11:58:25 INFO mapreduce.Job:  map 67% reduce 0%
        18/10/16 11:58:27 INFO mapreduce.Job:  map 68% reduce 0%
        18/10/16 11:58:31 INFO mapreduce.Job:  map 69% reduce 0%
        18/10/16 11:58:33 INFO mapreduce.Job:  map 70% reduce 0%
        18/10/16 11:58:37 INFO mapreduce.Job:  map 72% reduce 0%
        18/10/16 11:58:41 INFO mapreduce.Job:  map 73% reduce 0%
        18/10/16 11:58:44 INFO mapreduce.Job:  map 74% reduce 0%
        18/10/16 11:58:48 INFO mapreduce.Job:  map 75% reduce 0%
        18/10/16 11:58:50 INFO mapreduce.Job:  map 76% reduce 0%
        18/10/16 11:58:53 INFO mapreduce.Job:  map 77% reduce 0%
        18/10/16 11:58:54 INFO mapreduce.Job:  map 78% reduce 0%
        18/10/16 11:58:56 INFO mapreduce.Job:  map 79% reduce 0%
        18/10/16 11:59:00 INFO mapreduce.Job:  map 80% reduce 0%
        18/10/16 11:59:02 INFO mapreduce.Job:  map 81% reduce 0%
        18/10/16 11:59:05 INFO mapreduce.Job:  map 82% reduce 0%
        18/10/16 11:59:08 INFO mapreduce.Job:  map 83% reduce 0%
        18/10/16 11:59:11 INFO mapreduce.Job:  map 84% reduce 0%
        18/10/16 11:59:17 INFO mapreduce.Job:  map 85% reduce 0%
        18/10/16 11:59:23 INFO mapreduce.Job:  map 86% reduce 0%
        18/10/16 11:59:26 INFO mapreduce.Job:  map 88% reduce 0%
        18/10/16 11:59:29 INFO mapreduce.Job:  map 89% reduce 0%
        18/10/16 11:59:30 INFO mapreduce.Job:  map 90% reduce 0%
        18/10/16 11:59:35 INFO mapreduce.Job:  map 91% reduce 0%
        18/10/16 11:59:41 INFO mapreduce.Job:  map 92% reduce 0%
        18/10/16 11:59:42 INFO mapreduce.Job:  map 93% reduce 0%
        18/10/16 11:59:47 INFO mapreduce.Job:  map 94% reduce 0%
        18/10/16 11:59:48 INFO mapreduce.Job:  map 95% reduce 0%
        18/10/16 11:59:53 INFO mapreduce.Job:  map 96% reduce 0%
        18/10/16 11:59:54 INFO mapreduce.Job:  map 97% reduce 0%
        18/10/16 11:59:59 INFO mapreduce.Job:  map 98% reduce 0%
        18/10/16 12:00:00 INFO mapreduce.Job:  map 99% reduce 0%
        18/10/16 12:00:03 INFO mapreduce.Job:  map 100% reduce 0%
        18/10/16 12:00:05 INFO mapreduce.Job: Job job_1539682780316_0008 completed successfully
        18/10/16 12:00:05 INFO mapreduce.Job: Counters: 31
                File System Counters
                        FILE: Number of bytes read=0
                        FILE: Number of bytes written=592972
                        FILE: Number of read operations=0
                        FILE: Number of large read operations=0
                        FILE: Number of write operations=0
                        HDFS: Number of bytes read=344
                        HDFS: Number of bytes written=10000000000
                        HDFS: Number of read operations=16
                        HDFS: Number of large read operations=0
                        HDFS: Number of write operations=8
                Job Counters
                        Launched map tasks=4
                        Other local map tasks=4
                        Total time spent by all maps in occupied slots (ms)=901954
                        Total time spent by all reduces in occupied slots (ms)=0
                        Total time spent by all map tasks (ms)=901954
                        Total vcore-milliseconds taken by all map tasks=901954
                        Total megabyte-milliseconds taken by all map tasks=923600896
                Map-Reduce Framework
                        Map input records=100000000
                        Map output records=100000000
                        Input split bytes=344
                        Spilled Records=0
                        Failed Shuffles=0
                        Merged Map outputs=0
                        GC time elapsed (ms)=1643
                        CPU time spent (ms)=133870
                        Physical memory (bytes) snapshot=691634176
                        Virtual memory (bytes) snapshot=6322606080
                        Total committed heap usage (bytes)=930086912
                org.apache.hadoop.examples.terasort.TeraGen$Counters
                        CHECKSUM=214760662691937609
                File Input Format Counters
                        Bytes Read=0
                File Output Format Counters
                        Bytes Written=10000000000

        real    4m47.783s
        user    0m6.370s
        sys     0m0.609s

Check the files

        [daniramirez@sebc-vm2 hadoop-mapreduce]$ hdfs dfs -ls /user/DanielRamirezSanchez/terasort-input10G
        Found 5 items
        -rw-r--r--   2 DanielRamirezSanchez supergroup          0 2018-10-16 12:00 /user/DanielRamirezSanchez/terasort-input10G/_SUCCESS
        -rw-r--r--   2 DanielRamirezSanchez supergroup 2500000000 2018-10-16 11:59 /user/DanielRamirezSanchez/terasort-input10G/part-m-00000
        -rw-r--r--   2 DanielRamirezSanchez supergroup 2500000000 2018-10-16 12:00 /user/DanielRamirezSanchez/terasort-input10G/part-m-00001
        -rw-r--r--   2 DanielRamirezSanchez supergroup 2500000000 2018-10-16 11:59 /user/DanielRamirezSanchez/terasort-input10G/part-m-00002
        -rw-r--r--   2 DanielRamirezSanchez supergroup 2500000000 2018-10-16 11:59 /user/DanielRamirezSanchez/terasort-input10G/part-m-00003

Terasort command

        [daniramirez@sebc-vm2 hadoop-mapreduce]$ time sudo -u DanielRamirezSanchez hadoop jar hadoop-mapreduce-examples-2.6.0-cdh5.13.3.jar terasort /user/DanielRamirezSanchez/terasort-input10G /user/DanielRamirezSanchez/terasort_output10G
        18/10/16 12:01:27 INFO terasort.TeraSort: starting
        18/10/16 12:01:29 INFO input.FileInputFormat: Total input paths to process : 4
        Spent 213ms computing base-splits.
        Spent 5ms computing TeraScheduler splits.
        Computing input splits took 218ms
        Sampling 10 splits of 300
        Making 4 from 100000 sampled records
        Computing parititions took 10556ms
        Spent 10778ms computing partitions.
        18/10/16 12:01:39 INFO client.RMProxy: Connecting to ResourceManager at sebc-vm2.westeurope.cloudapp.azure.com/10.0.2.6:8032
        18/10/16 12:01:40 INFO mapreduce.JobSubmitter: number of splits:300
        18/10/16 12:01:40 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1539682780316_0009
        18/10/16 12:01:41 INFO impl.YarnClientImpl: Submitted application application_1539682780316_0009
        18/10/16 12:01:41 INFO mapreduce.Job: The url to track the job: http://sebc-vm2.westeurope.cloudapp.azure.com:8088/proxy/application_1539682780316_0009/
        18/10/16 12:01:41 INFO mapreduce.Job: Running job: job_1539682780316_0009
        18/10/16 12:01:55 INFO mapreduce.Job: Job job_1539682780316_0009 running in uber mode : false
        18/10/16 12:01:55 INFO mapreduce.Job:  map 0% reduce 0%
        18/10/16 12:02:13 INFO mapreduce.Job:  map 1% reduce 0%
        18/10/16 12:02:15 INFO mapreduce.Job:  map 2% reduce 0%
        18/10/16 12:02:28 INFO mapreduce.Job:  map 3% reduce 0%
        18/10/16 12:02:29 INFO mapreduce.Job:  map 4% reduce 0%
        18/10/16 12:02:34 INFO mapreduce.Job:  map 5% reduce 0%
        18/10/16 12:02:44 INFO mapreduce.Job:  map 6% reduce 0%
        18/10/16 12:02:52 INFO mapreduce.Job:  map 7% reduce 0%
        18/10/16 12:02:57 INFO mapreduce.Job:  map 8% reduce 0%
        18/10/16 12:03:08 INFO mapreduce.Job:  map 9% reduce 0%
        18/10/16 12:03:10 INFO mapreduce.Job:  map 10% reduce 0%
        18/10/16 12:03:13 INFO mapreduce.Job:  map 11% reduce 0%
        18/10/16 12:03:27 INFO mapreduce.Job:  map 12% reduce 0%
        18/10/16 12:03:28 INFO mapreduce.Job:  map 13% reduce 0%
        18/10/16 12:03:41 INFO mapreduce.Job:  map 14% reduce 0%
        18/10/16 12:03:45 INFO mapreduce.Job:  map 15% reduce 0%
        18/10/16 12:03:53 INFO mapreduce.Job:  map 16% reduce 0%
        18/10/16 12:03:58 INFO mapreduce.Job:  map 17% reduce 0%
        18/10/16 12:04:04 INFO mapreduce.Job:  map 18% reduce 0%
        18/10/16 12:04:11 INFO mapreduce.Job:  map 19% reduce 0%
        18/10/16 12:04:22 INFO mapreduce.Job:  map 20% reduce 0%
        18/10/16 12:04:23 INFO mapreduce.Job:  map 21% reduce 0%
        18/10/16 12:04:38 INFO mapreduce.Job:  map 22% reduce 0%
        18/10/16 12:04:41 INFO mapreduce.Job:  map 23% reduce 0%
        18/10/16 12:04:47 INFO mapreduce.Job:  map 24% reduce 0%
        18/10/16 12:04:58 INFO mapreduce.Job:  map 25% reduce 0%
        18/10/16 12:05:00 INFO mapreduce.Job:  map 26% reduce 0%
        18/10/16 12:05:11 INFO mapreduce.Job:  map 27% reduce 0%
        18/10/16 12:05:17 INFO mapreduce.Job:  map 28% reduce 0%
        18/10/16 12:05:20 INFO mapreduce.Job:  map 29% reduce 0%
        18/10/16 12:05:30 INFO mapreduce.Job:  map 30% reduce 0%
        18/10/16 12:05:35 INFO mapreduce.Job:  map 31% reduce 0%
        18/10/16 12:05:42 INFO mapreduce.Job:  map 32% reduce 0%
        18/10/16 12:05:52 INFO mapreduce.Job:  map 33% reduce 0%
        18/10/16 12:05:55 INFO mapreduce.Job:  map 34% reduce 0%
        18/10/16 12:06:04 INFO mapreduce.Job:  map 35% reduce 0%
        18/10/16 12:06:10 INFO mapreduce.Job:  map 36% reduce 0%
        18/10/16 12:06:13 INFO mapreduce.Job:  map 37% reduce 0%
        18/10/16 12:06:27 INFO mapreduce.Job:  map 38% reduce 0%
        18/10/16 12:06:28 INFO mapreduce.Job:  map 39% reduce 0%
        18/10/16 12:06:37 INFO mapreduce.Job:  map 40% reduce 0%
        18/10/16 12:06:45 INFO mapreduce.Job:  map 41% reduce 0%
        18/10/16 12:06:49 INFO mapreduce.Job:  map 42% reduce 0%
        18/10/16 12:06:59 INFO mapreduce.Job:  map 43% reduce 0%
        18/10/16 12:07:05 INFO mapreduce.Job:  map 44% reduce 0%
        18/10/16 12:07:12 INFO mapreduce.Job:  map 45% reduce 0%
        18/10/16 12:07:21 INFO mapreduce.Job:  map 46% reduce 0%
        18/10/16 12:07:27 INFO mapreduce.Job:  map 47% reduce 0%
        18/10/16 12:07:35 INFO mapreduce.Job:  map 48% reduce 0%
        18/10/16 12:07:41 INFO mapreduce.Job:  map 49% reduce 0%
        18/10/16 12:07:44 INFO mapreduce.Job:  map 50% reduce 0%
        18/10/16 12:07:57 INFO mapreduce.Job:  map 51% reduce 0%
        18/10/16 12:07:58 INFO mapreduce.Job:  map 52% reduce 0%
        18/10/16 12:08:10 INFO mapreduce.Job:  map 53% reduce 0%
        18/10/16 12:08:15 INFO mapreduce.Job:  map 54% reduce 0%
        18/10/16 12:08:19 INFO mapreduce.Job:  map 55% reduce 0%
        18/10/16 12:08:28 INFO mapreduce.Job:  map 56% reduce 0%
        18/10/16 12:08:34 INFO mapreduce.Job:  map 57% reduce 0%
        18/10/16 12:08:42 INFO mapreduce.Job:  map 58% reduce 0%
        18/10/16 12:08:49 INFO mapreduce.Job:  map 59% reduce 0%
        18/10/16 12:08:53 INFO mapreduce.Job:  map 60% reduce 0%
        18/10/16 12:09:05 INFO mapreduce.Job:  map 61% reduce 0%
        18/10/16 12:09:09 INFO mapreduce.Job:  map 62% reduce 0%
        18/10/16 12:09:15 INFO mapreduce.Job:  map 63% reduce 0%
        18/10/16 12:09:24 INFO mapreduce.Job:  map 64% reduce 0%
        18/10/16 12:09:29 INFO mapreduce.Job:  map 65% reduce 0%
        18/10/16 12:09:38 INFO mapreduce.Job:  map 66% reduce 0%
        18/10/16 12:09:45 INFO mapreduce.Job:  map 67% reduce 0%
        18/10/16 12:09:49 INFO mapreduce.Job:  map 68% reduce 0%
        18/10/16 12:09:58 INFO mapreduce.Job:  map 69% reduce 0%
        18/10/16 12:10:04 INFO mapreduce.Job:  map 70% reduce 0%
        18/10/16 12:10:13 INFO mapreduce.Job:  map 71% reduce 0%
        18/10/16 12:10:20 INFO mapreduce.Job:  map 72% reduce 0%
        18/10/16 12:10:22 INFO mapreduce.Job:  map 73% reduce 0%
        18/10/16 12:10:36 INFO mapreduce.Job:  map 74% reduce 0%
        18/10/16 12:10:39 INFO mapreduce.Job:  map 75% reduce 0%
        18/10/16 12:10:44 INFO mapreduce.Job:  map 76% reduce 0%
        18/10/16 12:10:55 INFO mapreduce.Job:  map 77% reduce 0%
        18/10/16 12:10:57 INFO mapreduce.Job:  map 78% reduce 0%
        18/10/16 12:11:08 INFO mapreduce.Job:  map 79% reduce 0%
        18/10/16 12:11:13 INFO mapreduce.Job:  map 80% reduce 0%
        18/10/16 12:11:22 INFO mapreduce.Job:  map 81% reduce 0%
        18/10/16 12:11:27 INFO mapreduce.Job:  map 82% reduce 0%
        18/10/16 12:11:39 INFO mapreduce.Job:  map 82% reduce 2%
        18/10/16 12:11:42 INFO mapreduce.Job:  map 83% reduce 2%
        18/10/16 12:11:46 INFO mapreduce.Job:  map 83% reduce 7%
        18/10/16 12:11:51 INFO mapreduce.Job:  map 84% reduce 7%
        18/10/16 12:11:52 INFO mapreduce.Job:  map 84% reduce 9%
        18/10/16 12:11:58 INFO mapreduce.Job:  map 84% reduce 12%
        18/10/16 12:12:04 INFO mapreduce.Job:  map 84% reduce 15%
        18/10/16 12:12:10 INFO mapreduce.Job:  map 85% reduce 15%
        18/10/16 12:12:13 INFO mapreduce.Job:  map 86% reduce 15%
        18/10/16 12:12:16 INFO mapreduce.Job:  map 86% reduce 17%
        18/10/16 12:12:17 INFO mapreduce.Job:  map 86% reduce 18%
        18/10/16 12:12:22 INFO mapreduce.Job:  map 86% reduce 19%
        18/10/16 12:12:28 INFO mapreduce.Job:  map 86% reduce 21%
        18/10/16 12:12:29 INFO mapreduce.Job:  map 87% reduce 22%
        18/10/16 12:12:47 INFO mapreduce.Job:  map 88% reduce 22%
        18/10/16 12:12:49 INFO mapreduce.Job:  map 89% reduce 22%
        18/10/16 12:13:10 INFO mapreduce.Job:  map 90% reduce 22%
        18/10/16 12:13:17 INFO mapreduce.Job:  map 90% reduce 23%
        18/10/16 12:13:20 INFO mapreduce.Job:  map 91% reduce 23%
        18/10/16 12:13:33 INFO mapreduce.Job:  map 92% reduce 23%
        18/10/16 12:13:41 INFO mapreduce.Job:  map 93% reduce 23%
        18/10/16 12:13:52 INFO mapreduce.Job:  map 94% reduce 23%
        18/10/16 12:14:00 INFO mapreduce.Job:  map 94% reduce 24%
        18/10/16 12:14:05 INFO mapreduce.Job:  map 95% reduce 24%
        18/10/16 12:14:10 INFO mapreduce.Job:  map 96% reduce 24%
        18/10/16 12:14:26 INFO mapreduce.Job:  map 97% reduce 24%
        18/10/16 12:14:39 INFO mapreduce.Job:  map 98% reduce 24%
        18/10/16 12:14:44 INFO mapreduce.Job:  map 99% reduce 24%
        18/10/16 12:14:47 INFO mapreduce.Job:  map 99% reduce 25%
        18/10/16 12:14:59 INFO mapreduce.Job:  map 100% reduce 25%
        18/10/16 12:15:00 INFO mapreduce.Job:  map 100% reduce 29%
        18/10/16 12:15:05 INFO mapreduce.Job:  map 100% reduce 46%
        18/10/16 12:15:06 INFO mapreduce.Job:  map 100% reduce 51%
        18/10/16 12:15:08 INFO mapreduce.Job:  map 100% reduce 54%
        18/10/16 12:15:11 INFO mapreduce.Job:  map 100% reduce 56%
        18/10/16 12:15:14 INFO mapreduce.Job:  map 100% reduce 57%
        18/10/16 12:15:17 INFO mapreduce.Job:  map 100% reduce 58%
        18/10/16 12:15:18 INFO mapreduce.Job:  map 100% reduce 59%
        18/10/16 12:15:20 INFO mapreduce.Job:  map 100% reduce 60%
        18/10/16 12:15:23 INFO mapreduce.Job:  map 100% reduce 62%
        18/10/16 12:15:24 INFO mapreduce.Job:  map 100% reduce 63%
        18/10/16 12:15:29 INFO mapreduce.Job:  map 100% reduce 64%
        18/10/16 12:15:30 INFO mapreduce.Job:  map 100% reduce 65%
        18/10/16 12:15:32 INFO mapreduce.Job:  map 100% reduce 66%
        18/10/16 12:15:36 INFO mapreduce.Job:  map 100% reduce 67%
        18/10/16 12:15:41 INFO mapreduce.Job:  map 100% reduce 68%
        18/10/16 12:15:42 INFO mapreduce.Job:  map 100% reduce 69%
        18/10/16 12:15:47 INFO mapreduce.Job:  map 100% reduce 70%
        18/10/16 12:15:48 INFO mapreduce.Job:  map 100% reduce 71%
        18/10/16 12:15:54 INFO mapreduce.Job:  map 100% reduce 72%
        18/10/16 12:15:59 INFO mapreduce.Job:  map 100% reduce 73%
        18/10/16 12:16:02 INFO mapreduce.Job:  map 100% reduce 74%
        18/10/16 12:16:05 INFO mapreduce.Job:  map 100% reduce 75%
        18/10/16 12:16:08 INFO mapreduce.Job:  map 100% reduce 76%
        18/10/16 12:16:17 INFO mapreduce.Job:  map 100% reduce 77%
        18/10/16 12:16:36 INFO mapreduce.Job:  map 100% reduce 78%
        18/10/16 12:16:54 INFO mapreduce.Job:  map 100% reduce 79%
        18/10/16 12:17:09 INFO mapreduce.Job:  map 100% reduce 80%
        18/10/16 12:17:27 INFO mapreduce.Job:  map 100% reduce 81%
        18/10/16 12:17:33 INFO mapreduce.Job:  map 100% reduce 89%
        18/10/16 12:17:36 INFO mapreduce.Job:  map 100% reduce 90%
        18/10/16 12:17:45 INFO mapreduce.Job:  map 100% reduce 91%
        18/10/16 12:18:10 INFO mapreduce.Job:  map 100% reduce 92%
        18/10/16 12:18:30 INFO mapreduce.Job:  map 100% reduce 93%
        18/10/16 12:18:33 INFO mapreduce.Job:  map 100% reduce 94%
        18/10/16 12:18:45 INFO mapreduce.Job:  map 100% reduce 95%
        18/10/16 12:18:57 INFO mapreduce.Job:  map 100% reduce 96%
        18/10/16 12:19:04 INFO mapreduce.Job:  map 100% reduce 97%
        18/10/16 12:19:10 INFO mapreduce.Job:  map 100% reduce 98%
        18/10/16 12:19:16 INFO mapreduce.Job:  map 100% reduce 99%
        18/10/16 12:19:21 INFO mapreduce.Job:  map 100% reduce 100%
        18/10/16 12:19:22 INFO mapreduce.Job: Job job_1539682780316_0009 completed successfully
        18/10/16 12:19:22 INFO mapreduce.Job: Counters: 49
                File System Counters
                        FILE: Number of bytes read=4450186232
                        FILE: Number of bytes written=8838550880
                        FILE: Number of read operations=0
                        FILE: Number of large read operations=0
                        FILE: Number of write operations=0
                        HDFS: Number of bytes read=10000051600
                        HDFS: Number of bytes written=10000000000
                        HDFS: Number of read operations=912
                        HDFS: Number of large read operations=0
                        HDFS: Number of write operations=8
                Job Counters
                        Launched map tasks=300
                        Launched reduce tasks=4
                        Data-local map tasks=300
                        Total time spent by all maps in occupied slots (ms)=4415386
                        Total time spent by all reduces in occupied slots (ms)=1394064
                        Total time spent by all map tasks (ms)=4415386
                        Total time spent by all reduce tasks (ms)=1394064
                        Total vcore-milliseconds taken by all map tasks=4415386
                        Total vcore-milliseconds taken by all reduce tasks=1394064
                        Total megabyte-milliseconds taken by all map tasks=4521355264
                        Total megabyte-milliseconds taken by all reduce tasks=1427521536
                Map-Reduce Framework
                        Map input records=100000000
                        Map output records=100000000
                        Map output bytes=10200000000
                        Map output materialized bytes=4342785279
                        Input split bytes=51600
                        Combine input records=0
                        Combine output records=0
                        Reduce input groups=100000000
                        Reduce shuffle bytes=4342785279
                        Reduce input records=100000000
                        Reduce output records=100000000
                        Spilled Records=200000000
                        Shuffled Maps =1200
                        Failed Shuffles=0
                        Merged Map outputs=1200
                        GC time elapsed (ms)=42337
                        CPU time spent (ms)=1127310
                        Physical memory (bytes) snapshot=141930229760
                        Virtual memory (bytes) snapshot=481606021120
                        Total committed heap usage (bytes)=168995848192
                Shuffle Errors
                        BAD_ID=0
                        CONNECTION=0
                        IO_ERROR=0
                        WRONG_LENGTH=0
                        WRONG_MAP=0
                        WRONG_REDUCE=0
                File Input Format Counters
                        Bytes Read=10000000000
                File Output Format Counters
                        Bytes Written=10000000000
        18/10/16 12:19:22 INFO terasort.TeraSort: done

        real    17m55.581s
        user    0m11.058s
        sys     0m1.353s


Check the files

        [daniramirez@sebc-vm2 hadoop-mapreduce]$ hdfs dfs -ls /user/DanielRamirezSanchez/terasort_output10G
        Found 6 items
        -rw-r--r--   1 DanielRamirezSanchez supergroup          0 2018-10-16 12:19 /user/DanielRamirezSanchez/terasort_output10G/_SUCCESS
        -rw-r--r--  10 DanielRamirezSanchez supergroup         33 2018-10-16 12:01 /user/DanielRamirezSanchez/terasort_output10G/_partition.lst
        -rw-r--r--   1 DanielRamirezSanchez supergroup 2498126900 2018-10-16 12:16 /user/DanielRamirezSanchez/terasort_output10G/part-r-00000
        -rw-r--r--   1 DanielRamirezSanchez supergroup 2500978500 2018-10-16 12:18 /user/DanielRamirezSanchez/terasort_output10G/part-r-00001
        -rw-r--r--   1 DanielRamirezSanchez supergroup 2514446100 2018-10-16 12:18 /user/DanielRamirezSanchez/terasort_output10G/part-r-00002
        -rw-r--r--   1 DanielRamirezSanchez supergroup 2486448500 2018-10-16 12:19 /user/DanielRamirezSanchez/terasort_output10G/part-r-00003
