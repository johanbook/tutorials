# Scanning

I will here show some examples of how to use the tool `nmap` to scan network or
host.

## Finding router IP

Use `route -n` to find your router. It is the gateway with a destination of
`0.0.0.0`.

## Scanning ports

Given an IP we scan its ports using `nmap <ip>`.

NB: Mobile devices typically do not expose any ports.
