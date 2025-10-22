
    Which program is fastest? Is it always the fastest?
    Which program is slowest? Is it always the slowest?
    Was there a trend in program execution time based on the size of data in each Node? If so, what, and why?
    Was there a trend in program execution time based on the length of the block chain?
    Consider heap breaks, what's noticeable? Does increasing the stack size affect the heap? Speculate on any similarities and differences in programs?

make clean breaks  MIN_BYTES=100 MAX_BYTES=1000 NUM_BLOCKS=10000000
alloca.out:        69
list.out:          49115
malloc.out:        47340
new.out:           49115



    Considering either the malloc.cpp or alloca.cpp versions of the program, generate a diagram showing two Nodes. Include in the diagram
        the relationship of the head, tail, and Node next pointers.
        show the size (in bytes) and structure of a Node that allocated six bytes of data
        include the bytes pointer, and indicate using an arrow which byte in the allocated memory it points to.
    There's an overhead to allocating memory, initializing it, and eventually processing (in our case, hashing it). For each program, were any of these tasks the same? Which one(s) were different?
    As the size of data in a Node increases, does the significance of allocating the node increase or decrease?

