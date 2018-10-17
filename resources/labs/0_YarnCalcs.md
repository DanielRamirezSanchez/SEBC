Modified the numbers existing in the Excel file

	Worker vcores   20
	Worker spindles 12
	Worker RAM  128
	Workload factor 2
	Worker nodes    10

Modified the formula for the OS Memory, since it seemed to high

	=PRODUCT(0.1,B3) modified to =PRODUCT(0.04,B3), because a number nearby 5GB of RAM for the OS would be more balanced.


What criteria affects the workload factor?
	
	The workload factor is representing how many mappers and reducres we can run in each of the worker nodes. So if the workload is 1, we will run 1 map task per worker node, 2 will run 2 and 4 will run 4. Exactly the same in the case of the reducers.

	In the Excel file, we calculate the following things:
		- How many mappers/reducers we can run with the current amount of cores / how many cores a map consumes
		- How many mappers/reducers we can run with the current amount of available memory / how much memory a map consumes
		- The workload factor multiplied by the number of nodes

	The minimum of those 3 calculations is what is going to determine the quantity of maps and reduces that we will be able to run in the cluster. Because it might be limited byt memory, by cpu or by the workload factor, depending on the structure of the cluster.

	In this example, by setting the workload factor to 2, we could theoretically run up untill 20 mapper tasks, but we only have 15 cores, and each map consumes 1 core so the real amount of mappers we could possibly run is 15. Because the CPU is limiting the cluster in this case.