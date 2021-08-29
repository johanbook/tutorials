# MITM

Man In The Middle attacks (MITM) are when a untrusted actor listens to (or more
commonly forwards) traffic between two communicating partners A and B.

## Breaking TLS

If the MITM is present during an initial TLS handshake, that handshake can be
compromised by the MITM issuing one TLS connection to target B and one to A.
