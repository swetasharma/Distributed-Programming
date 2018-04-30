# Distributed-Programming

The structure of dictributed computer: there are processors P0, P1. and there are multiple computers, each with cores, connected through a network, amd also containing storage in each computer node.

Map - Reduce: pattern of parallel functional programming that has been bery successfule in enabling big data comoutrations.
Grouping is performed automatically by the map reduce framework.
It folds or reduces all those values to obtain a single output key-value pair for each key k

Apache Hadoop ( used for Distributed MapReduce ):
In distributed computing you connect multiple computers with a network.
each of these computers has some storage.
we want to write parallel program that operate on this distributed data.
The map reduce program specifies a map function f and a reduce function g andthis will generate a large set of map tasks and reduce tasks that are then scheduled by the system. thats a key part ofthe hadoop framework, that will take care of executing  the tasks that are generated from your MapReduce program. these are the tasks that perform the map computation and reduce computations.

Fault Tolerance : what this means if a computer fails during the execution of a big data application. It will be possible to reexecute the tasks that did not complete successfully. and the reasom this works is map reduce is essentially a funcitonal proramming paradigm. so if you are in the middle of a map task and reduce task, it did not complete, you can reinitiate ot with the same input and you will get the same output. Thats not true for parallel program in general because if they are actually modifying some state, then reexecuting it nay result in a different answer. But for Map reduce it just works fine.

prople write higher level of query languages  that automatiocally get  translated to MapReduce programs (Languahes like : HIVE, PIG)

large document could be distribuited as key value pair


Input K-V pairs -> Intermeduiate key value pairs -> group -> reduce -> output key valu pairs popular exampple is word count(used for document mining and text mining)

The main benefit is that uou have large volumes of data, you pull it in, perform the map function, perform the reduce,and then push out the large volumes of data back to you storage and you can really processiign terabytes of data quite easily that way. This has been used for algorithms such as page rank for generating index for web searches.

Apache Spark:
One of the key motivation for creating the Apache Spark Project, was the observation that each of these computers also has memory.and when yuou are procesing data you dont have to always read and write out of disk. If you have enough mememory you can keep the intermediate values in memory and then perform repeated computations on them.
In Hadoop it was simpler the memory really wasn't used for much beyond just a temporary buffer and was really used to stream data from disks into the computer, perform the map and reduce operations, and stream the results back into the disk.


Changes that have occured when movnng from Hadoop to spark:(Hadoop -> Spark)
1. K-V pair -> Reselient Distributed DataSet (RDD).(allow yo to store data in other forms.)
2. M-R -> General ops 
     - TRANSFORMS (INTERMEDIATE OPS) (MAP. FILTER, JOIN)
     - ACTIONS (TERMONAL OPS) REDUCE, COLLECT)
     taken these concepts pretty much sililar to javastreams
     
Some key innovation:
1. Lazy evaluation:
2. Caching (Memory):
     
     
     
     













 

