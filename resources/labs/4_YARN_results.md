My first execution went terribly slow. In part because of the disk (I'm using HDDs, not SSD), and also because of the replication.

	[daniramirez@sebc-vm2 resourcesLab]$ ./YARNtest.sh
	Testing loop started on Tue Oct 16 17:22:23 UTC 2018
	----------- New Test -----------
	#Mapper/s =  4
	#Reducer/s =  2
	Memory =  512


	Starting Teragen

	real    21m57.416s
	user    0m10.315s
	sys     0m1.397s


	Starting Terasort

	real    87m50.191s
	user    0m21.114s
	sys     0m4.628s
	Deleted /results/tg-10GB-4-2-512
	Deleted /results/ts-10GB-4-2-512
	----------- End Test -----------


Once I change the script to avoid replication in the generation of data the numbers improved.

My worst execution has been with 3 mappers, 3 reducers and 1024MB of memory (I've had other executions with worse times for Teragen, but still this one wins because of the Terasort duration):

	[daniramirez@sebc-vm2 resourcesLab]$ ./YARNtest.sh
	Testing loop started on Wed Oct 17 13:35:33 UTC 2018
	----------- New Test -----------
	#Mapper/s =  3
	#Reducer/s =  3
	Memory =  1024


	Starting Teragen

	real    9m2.899s
	user    0m7.786s
	sys     0m0.815s


	Starting Terasort

	real    48m1.942s
	user    0m16.545s
	sys     0m2.747s
	Deleted /results/tg-10GB-3-3-1024
	Deleted /results/ts-10GB-3-3-1024
	----------- End Test -----------

On the other hand, my best configuration has been 8 mappers, 1 reducer and 1024MB of memory.

	[daniramirez@sebc-vm2 resourcesLab]$ ./YARNtest.sh
	Testing loop started on Wed Oct 17 14:33:58 UTC 2018
	----------- New Test -----------
	#Mapper/s =  8
	#Reducer/s =  1
	Memory =  1024


	Starting Teragen

	real    10m3.311s
	user    0m7.781s
	sys     0m0.811s


	Starting Terasort

	real    17m53.069s
	user    0m10.763s
	sys     0m1.317s
	Deleted /results/tg-10GB-8-1-1024
	Deleted /results/ts-10GB-8-1-1024
	----------- End Test -----------
	Testing loop ended on Wed Oct 17 15:02:00 UTC 2018

Through all my test, I have seen that the Teragen is a lot more stable to the changes in the configuration, while the Terasort can change drastically depending on the number of mappers and reducers selected for the job to run. As you can see in the results.