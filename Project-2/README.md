## Computing a Mean Questions

here is a graph of the speedup of the "computing a mean" project versus the number of threads:

![graph of speedup vs threads for computing a mean](MeanSpeedup.png)

**Does the graph“converge” to some general value? What’s the maximum speedup you got from threading? What happens when you use more cores than are available in the hardware?**

The graph converges to around 20x speedup. The maximum speedup was 20.5x speedup at 64 threads. 
when there are more threads than available not much happens to the speedup. The speedup starts getting worse at around 70 threads where the max available on the system is 72. When requesting more threads than available on the system the computer has to wait for a thread to be available before processing the current thread. In this case it doesn't seem to impact efficiency much when it is a reasonable value. however running the same program with 8500000 threads makes blue (SSU's sever) very unhappy.

**Considering the number of cores in the system, do you get a linear scaling of performance as you add more cores?**

You dont get a linear scaling of preformance for each core. Based on the shape of the curve the speedup looks like its based on the log of the number of threads.



**In parallel computation, there’s a maximum speed up you can achieve that’s described by Amdahl’s Law

    Links to an external site.. The law considers the time a program takes to run as the sum of the serial part (the part of the code that can’t or isn’t parallelized, like reading files), and the parallelized part, which can mathematically be written as

T = (1- p)T + pT

where p is the percentage of the program that is parallelized. When the parallel parts of the program are run using n threads, the timing becomes

T = (1 - p)T + \frac{p}{n}T

If you used an infinite number of processors, the \frac{p}{n}T would approach zero, as the runtime is dominated by the serial part. You can see this on the graph, as adding more threads doesn’t continue to decrease the runtime. Looking at your graph, what value would you proposed for p, and describe how you arrived at that value**

p would equal ~0.95. To find p I took the time with the greatest speedup, which was 1.61 and divided it
by the single threaded time. I then subtracted that value from one
I did the following steps:
I found the serialized time (1-p)T to be 1.61, the time with the greatest speedup.  
I then solved for p, and got it in the form, p = 1-(1.61/T)  
Plug in in the single threaded time 33.05 for T, I got p = 0.95.  

so ~95% of the program can be parallelized. 


**consider the kernel of the mean computation. How many bytes of data are required per iteration? What’s the associated bandwidth used by the kernel? Is that value consistent when you consider threaded versions?**

Each value in Data is a float, which is 8 bytes. so for every kernel run, 8 Bytes are required.


for 8,500,000,000 iterations in 33.05s that works out to 
singlethreading:
8bytes\*(8,500,000,000)/33.05s =2050000000bytes/sec or 2.05GB/s

with multithreading that becomes
8bytes\*(8,500,000,000)/1.61s =4220000000bytes/sec or 42.2GB/s


The value makes sense given there is a roughtly 20x speedup, so the bandwidth would be roughly 20x faster.

