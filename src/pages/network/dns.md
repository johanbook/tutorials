# Domain Name System

In order to communicate with another device, such as a website, one needs to
know the target's [IP address](ip_address), however, this has several
difficulties:

- The target's IP address might change (e.g. it can be served by a machine on
  another network).
- IP addresses are very difficult to parse and remember to humans.

To address these weaknesses, one introduced a system to associate names to the
IP addresses, such as `https://my-website.com` corresponds to
`https://127.0.0.1`. This name resolution is handled by a DNS server, which a
machine one can connect to in order look up a domain name (that process is
called a NS lookup).

## Look up

First the root DNS is queried, then the TLD (Top-Level Domain), then then the
domain and then the subdomain and so on.

## Record Types

A DNS provider has a list of different records. There are different types of
records. Some common record types are

- **A** Points to an IPv4 address.
- **AAAA** Points to an IPv6 address.
- **ALIAS** Points to another DNS name.
- **CNAME** Points to another DNS name. Should not be used for apex domains.
- **SOA** Stores domain metadata. One can manually fetch the SOA record of a
  domain by doing `dig +short soa <DOMAIN>`.
- **DS** Stands for Delegation of Signing and is used in DNSSEC. If there is no
  DS record, then DNSSEC is not enabled.
- **MX** Mail Exchange record for mail servers.
- **NS** Indicates which nameserver is authoritative for a given domain.

## DNSSEC

DNSSEC stands for DNS Security Extensions is a suite of extensions that aim to
add some security to the DNS protocol. It can protect against e.g. DNS cache
poisoning.

DNSSEC relies on a chain of trust as each domain is signed.
