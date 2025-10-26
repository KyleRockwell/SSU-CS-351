
 ## Which program is fastest? Is it always the fastest?
- In general malloc.cpp and alloca.cpp were the fastest.

## Which program is slowest? Is it always the slowest?
- new.cpp is usalually slowest, though sometimes it is tied or very close to list.cpp

 ## Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?
 - It looks as the size of data in each node gets bigger, the time difference between each program gets smaller.
 - It might be because the time it takes to hash each value is significantly longer than the time it takes to allocate memory.
     
## Was there a trend in program execution time based on the length of the block chain?
-  The program execution time  increases roughly linearly with the length of the blockchain. 

- with  `make clean trials OPT="-O3"  MIN_BYTES=200 MAX_BYTES=20000 NUM_BLOCKS=100000` the average execution time for all the programs was 2.213 seconds.

- with `make clean trials OPT="-O3"  MIN_BYTES=200 MAX_BYTES=20000 NUM_BLOCKS=1000000` the average execution time for all the programs was
22.5 seconds.

- addtionally with this trial, malloc.cpp was the fastest with an average time of 21.308 seconds, compared to alloca.cpp which had the slowest time at 23.512 seconds


## Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?

With the number of bites less than or equal to 13, it looks like the number of heap breaks does not increase at all, regardless of the lenght of the  blockchain. 
```
alloca.out:        69
list.out:          75
malloc.out:        73
new.out:           75
```
in fact It seems as though the length of the blockchain does not increas the number of heap breaks at all.
with both make clean breaks `MIN_BYTES=10 MAX_BYTES=1000 NUMBLOCKS=1000000000000` and `make clean breaks MIN_BYTES=10 MAX_BYTES=1000 NUMBLOCKS=1` having the same number of heap breaks. 

It becomes more clear that alloca doesnt use the stack to allocate memory, since the number of heap breaks remains a constant 69 while the other programs have increased significantly. Additionally list and new both have the same number of heap breaks with all the trials I have run, leading me to believe they both call the same function in the same way to allocate heap memory.
```

   make clean breaks  MIN_BYTES=100 MAX_BYTES=1000 NUM_BLOCKS=10000000
   alloca.out:        69
   list.out:          49115
   malloc.out:        47340
   new.out:           49115
  
```





## Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes. Include in the diagram the relationship of the head, tail, and Node next pointers.
![malloc.cpp nodes](https://raw.githubusercontent.com/KyleRockwell/SSU-CS-351/refs/heads/main/Project-1/2%20nodes.png)


## show the size (in bytes) and structure of a Node that allocated six bytes of data include the bytes pointer, and indicate using an arrow which byte in the allocated memory it points to.
![malloc.cpp node of 6 bytes](https://raw.githubusercontent.com/KyleRockwell/SSU-CS-351/refs/heads/main/Project-1/1%20node.png)


## There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?
for `new.cpp` and `list.cpp` allocating initializing are part of the same process. For all programs the hashing step was the same. 

## As the size of data in a Node increases, does the significance of allocating the node increase or decrease?
the cost of allocating a node shouldn't increase compared to the cost of processing the data. 

