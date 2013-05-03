jinda
=====

Java distributed spaces

Why? Gelernter described the original vision. 

Why not? Stuff like JCS, memcache, ehcache, hazelcast, river, terracotta, gigaspaces, blitz, java tuplespaces, 
tibco activespaces, infinispan, Jboss cache, and many more are out there, but I find them hard to access,
although hazelcast access looks easiest.

Sounds like everything is reinventing UNIX filters and forks. Here's another UNIX reinvention.

I want a jar that is very simple and can do everything everywhere.

Client Actions (the filters): put, get, take, browse, listen
Server Actions (the forks): auto discovery, auto copy (distribute), auto heal

