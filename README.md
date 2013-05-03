Jinda
=====

Kind of Java distributed spaces. Kind of asynchronous sockets.

Why? Gelernter described the original vision. 

Why not? Stuff like JCS, memcache, ehcache, hazelcast, river, terracotta, gigaspaces, blitz, java tuplespaces, 
tibco activespaces, infinispan, Jboss cache, and many more are out there, but I find them hard to access. I have
certain requirements I want to achieve and everything seems to do everything, but in a too complicated or a too
commercial way.

Hazelcast was simplest and easiest at just a few jars, and it meets some of my requirements. 
The gigaspaces community download was 144 Mb, what????

To me it seems like everything is reinventing UNIX, particularly filters and forks, although in a more 
distributed fashion. Both processes and data are distributed.

So it's another UNIX reinvention in Java: I just want one or two jars that are very simple.
In the UNIX tradition of do one thing and do it well, the jar is a collection of single requirements. Those
requirements are:

Client requirements (the filters): put, get, take, browse, listen

Server requirements (the forks): auto discovery (monitor), auto copy (distribute), auto availability (self heal)

Performance (the speed): The space and all the processes that use the space run on the same server wherever possible

If the Jinda monitor can find all the required processes and data on the same box then those are the set 
made available. If not, then Jinda monitor searches for those required processes and data available through all 
the boxes on the cluster, and makes the set available that provides the highest throughput.

When the primary box goes down the secondary Jinda realises and kicks in, which in turn creates another secondary 
of itself on some other box available to it in the cluster. If the whole cluster goes down a Jinda on a DR box in
another cluster can take over as primary.
