# Load balancers

A load balancer is a network component that routes incoming load to different
targets. This can be done on both hardware and software level.

A load balancer needs to keep track of its target services. This can be done by
e.g. each service registering when spinning up and unregestering when spinning
down.

## Selection strategy

There are various techniques for how the load distribution is decided. Some
examples are:

- One often uses a Round Robin approach (each service taking a turn
  sequentially). One can also incorporate weighing depending on service
  throughput or health checks.
- One can also hash ip of incoming traffic to decide how it is routed (which is
  very useful if one also uses caching or some server-side session). For cache
  dependent servers, consistent or rendezvous hashing is a good option.
- Base it on HTTP path name. This allows for using different servers for
  different paths, which can be useful when rolling out new code that only
  affects some paths.
