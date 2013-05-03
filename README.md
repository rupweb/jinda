Jinda
=====

Kind of Java distributed spaces, kind of asynchronous sockets, kind of process cache, kind of mirror for both data 
and processes that use the data.

Why? Gelernter described the original vision. 

Why not? Stuff like JCS, memcache, ehcache, hazelcast, river, terracotta, gigaspaces, blitz, java tuplespaces, 
tibco activespaces, infinispan, Jboss cache, and many more are out there for data, but I find them hard to access.
Not sure what's out there as a distributed process cache. I have certain requirements I want to achieve and 
everything seems to do everything, but in a too complicated or a too commercial way.

Hazelcast was simplest and easiest data mirror at just a few jars, and it meets some of the data requirements. 
The gigaspaces community download was 144 Mb, what????

It feels like it's all UNIX reinvention, particularly filters and forks, but perhaps in a more distributed fashion.
In Jinda both processes and data are distributed.

So it's a bit of a UNIX reinvention in Java: I just want one or two jars that are very simple. In the UNIX 
tradition of do one thing and do it well, the jar is a collection of single requirements. Those requirements are:

Client requirements (the pipes and filters): process start, process stop, data put, data get

Server requirements (the forks): auto discovery (monitor), auto copy (distribute), auto availability (self heal)

Performance (the speed): The space and all the processes that use the space run on the same server wherever possible
BUT

where the Jinda monitor can find the required processes and data sets on the same box then those are the sets 
made available. If a process fails, the Jinda monitor finds and starts the required processes and data sets
available through all the boxes on the cluster, attempting to make the set available that provides the lowest latency
and highest throughput. If the data corrupts the Jinda dumps the most recent input to file and becomes available 
again.

When the primary box goes down the secondary Jinda realises and kicks in, making all required processes and data
sets available, but further distributing another secondary of itself (of the data space and all the processes 
that it knows use the data space) on to some other box available to it in the cluster. If the whole cluster goes 
down a Jinda on a DR box in another cluster can take over as primary.

Alternatively processes can be managed from some other monitor, and Jinda is simply configured to distribute and 
manage data.

See the Wiki for more stuff.
