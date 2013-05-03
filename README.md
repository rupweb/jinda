Jinda
=====

Kind of Java distributed spaces. Kind of like hazelcast.

Why? Gelernter described the original vision. 

Why not? Stuff like JCS, memcache, ehcache, hazelcast, river, terracotta, gigaspaces, blitz, java tuplespaces, 
tibco activespaces, infinispan, Jboss cache, and many more are out there, but I find them hard to access. I have
certain requirements I want to achieve and everything seems to do everything, but in a too complicated or a too
commercial way.

Hazelcast was simplest and easiest. Gigaspaces community download was 144 Mb, what????

To me it seems like everything is reinventing UNIX, particularly filters and forks, although in a more 
distributed fashion?

Well here's another UNIX reinvention in Java: I just want a jar that can do everything everywhere but is very simple.
In the UNIX tradition of do one thing and do it well, the jar is a collection of single requirements. Those
requirements are:

Client requirements (the filters): put, get, take, browse, listen

Server requirements (the forks): auto discovery, auto copy (distribute itself), auto heal

Performance (the speed): As if shared memory on the same server. Basically as if everything was on the same box. 
When the primary box goes down everything in the Jinda auto heals to the secondary which creates another secondary
of itself on another box in the cluster. It's as if the Jinda becomes the JVM and forks itself. In other words the
Jinda knows every Java process registered with it, which it auto replicates to a secondary.
