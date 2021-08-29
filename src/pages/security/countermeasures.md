# Countermeasures

To tighten the security of a system there are various measures one can use.

## Security By Design

Software are designed with security in mind.

- **Principle of least privilege** A system component should not have access to
  more than what it needs.

## Firewall

A firewall is a networking middleware that decides what traffic should be
allowed into and out of a network node. A firewall can check

- Communication Protocol
- Ports
- IP Address

It can also use connection tracking.

For Linux based systems there is (as of now) `iptables` that is a complete
firewall. There is also `ufw` for a simplified interface to `iptables`.

## User Access Controls

Tightening user access.

## User Training

Train users in security. For example, they can be educated in social
engineering.

## Defense in Depth

If running a microservice system, instead of relying only on on global
authentication happening in the API gateway, each service should need to
authenticate when communicating with any other service.
