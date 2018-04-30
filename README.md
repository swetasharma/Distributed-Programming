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
     - TRANSFORMS (INTERMEDIATE OPS) (MAP, FILTER, JOIN)
     - ACTIONS (TERMONAL OPS) REDUCE, COUNT, COLLECT)
     taken these concepts pretty much sililar to javastreams
     
Some key innovation:
1. Lazy evaluation: Intermediate operations are performed lazily i.e. their evaluation is postponed to the point when a terminal
actions needs to be performed.

2. Caching (Memory): When you pull in the data into memory you can keep it there and use it for multiple operations.multiple transforms,
ending with an action, while the data is in memory. This gives a significanmt prders of magnitude performance improvenment becuase you are reading and writing data from memory for these intermediate operations instead of going to disk each time.
Sometimes in cloud computing it can be more expensive to use nodes with large  amount of memory than to use nodes with less memory. si thats a bit of a cost trade off but the performnance benefit is very clear.

you can write Spark programs in java becuase after all that infrastructure all runs on the same java virtual machine,
Implementation of Word count example in Spark using Java APIs:
1. Create new java spark context.
2. Input = sc.textfile ("here you can provide file name") were each line is object in RDD.
3. Words = input.flatmap ((line -> line.split("_"))) the map operation as to how we want to split a line into words.
4. pairs = words.maptopair((x) -> new tuple2(x,1)) represents one occurence of the word.emits pairs of the form (word, 1)
5. counts = pairs.reduceByKey((x,y) -> x+y )  to finally accumulate the count
here we have specified the map and reduce functions as lambdas.

we can really take the idea behind something like java streams and extend that to general operations and distributed data sets in the spark framwork, which could include the map reduce operations that you can do with Hadoop, but could include many more kinds of operations and with this ability to cache data in memory, we see opportunities to perform all kind of algorithms, including very interesting and machine learning algorithms on distributed computers.




















     
     
     
     













 

