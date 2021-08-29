---
title: DHCP
layout: ../../layouts/Article.astro
---

# DHCP

Dynamic Host Configuration Protocol (DHCP) is a protocol for dynamically assign
IP addresses. A device gets an IP from a DHCP server. Can also assign DNS,
default gateway and network mask. IP addresses are given as time-limited leases.

For example, one can run a DHCP query using the network utility `nmap` as done
below.

```sh
sudo nmap --script broadcast-dhcp-discover
Starting Nmap 7.92 ( https://nmap.org ) at 2021-08-23 13:45 CEST
Pre-scan script results:
| broadcast-dhcp-discover:
|   Response 1 of 1:
|     Interface: wlp0s20f3
|     IP Offered: 192.168.1.103
|     DHCP Message Type: DHCPOFFER
|     Server Identifier: 192.168.1.1
|     IP Address Lease Time: 1d00h00m00s
|     Subnet Mask: 255.255.255.0
|     Router: 192.168.1.1
|_    Domain Name Server: 192.168.1.1
WARNING: No targets were specified, so 0 hosts scanned.
Nmap done: 0 IP addresses (0 hosts up) scanned in 11.32 seconds
```
