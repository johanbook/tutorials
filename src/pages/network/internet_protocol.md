# Internet Protocol

The Internet Protocol (IP) is a protocol for delivering data from one computer
to another. It accomplishes this by dividing the data into small packages, each
containing a header with target destination and a data body. Each package is
then forwarded through the optimal route for the network and arrives at its
destination, but not necessarily in the original order (which is added in
[TCP](tcp)).

The computers that are part of a network can see all data being transmitted over
the network. Hence, when wanting to transmitting themselves it is possible that
that the network already is in use. If this is the case, they wait a random time
and checks if its free. The reason the time is random is in case several
computers are waiting and to avoid that they all wakes up and tries to connect
at the same time.

One upside with IP, is that it allows parts of a network to become a
sub-network, where a switch (or router) decides what communication goes between
the parent and child network. This reduces network traffic, as not all traffic
on the parent network is forwarded to the child and so on. It also alleviates
the requirement of global node IDs, as a node only need to have a unique id
inside its local network.
