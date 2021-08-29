# Tor

Tor, short for The Onion Router, is an approach for anonymous communication. If
A wishes to talk to B, then it will let the connection go through C. C is itself
a series of nodes (commonly called a Tor network). If the communication is
passed through three nodes in C, then each package A sends through C is
encrypted three times over, such that each node only knows its encrypted content
and the path to the next node. Om the way back the exact opposite happens. This
means that if a Tor node is captured (assuming it is not an input or exit node)
the capturer cannot tell who A or B are nor what they communicate about. If an
outsider is sniffing on both the input and exit nodes between A and B, then one
can deduce what traffic is between them by considering the times of the
packages.

Each package (called cells) sent inside the Tor network are of the same size and
will look equivalent if inspected externally.

## Hidden services

There can be hidden services inside the Tor network. These are often called
onion sites and use the `.onion` domain. In order to connect to such a site, one
needs to know the onion address - something that is typically not public.

## Using Tor

If using Tor, one's ISP can see that one is using Tor which may raise eyebrows.
However, this can be mitigated by using a [VPN](vpn) to connect to Tor.
