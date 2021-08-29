# Denial of Service

DoS (Denial of Service). A target is flooded with requests, causing it either
slow down answering legitimate requests or going down completely. These attacks
can be both fast and slow.

## Types

Here are a few different versions of DoS.

### DDos

Multiple computers simultaneously DoS a target. Often used with bot nets.

### ADos

There also ADoS (Amplified Denial of Service) attacks where one uses a server to
amplify the attack.

### Slow Loris

The Slow Loris attack attempts to keep a HTTP connection open with a server. It
does this by sending a HTTP request but omitting the carriage return indicating
the end of the request. Then the attacker periodically sends additional data in
the same connection such that the server never closes it.

This is especially severe in synchronous servers where a new thread is opened
for each concurrent connection.

## Countermeasures

There are various measures one can take to counter DoS:

- **Ratelimiting** The most basic approach is to cap the number of allowed
  requests per client. One can ratelimit on IP, username or even geographic
  region. Does not necessarily stop DDos though.
- **Autoscaling systems** If the system can scale after demand it might handle
  attacks better.
- **Challenges** If under a possible DoS attack, one can serve challenges to
  each unique client. Client that complete the challenge are then prioritized.
