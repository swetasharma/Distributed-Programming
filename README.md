# Distributed-Programming

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




 

