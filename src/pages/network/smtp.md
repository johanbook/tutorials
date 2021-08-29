# SMTP

Simple Mail Transfer Protocol (SMTP) is a stateful protocol for mail exchange.

## Commands

- `HELO`: Present own identity.
- `MAIL FROM`: Present own email address.
- `RCPT TO`: Send target email address.
- `DATA`: Send data.
- `QUIT`: Cancel connection.

## Status codes

Similar to [HTTP](http) each data transmission has a status code. For example,
the code 250 signals OK.

## Example

```
> telnet mail.mydomain.com
220 mail.mydomain.com ESMTP Postfix
> HELO server.otherdomain.com
250 server.otherdomain.com, I am glad to meet you
> MAIL FROM: <email@email.com>
250 OK
> RCPT TO: <email@email.com>
250 OK
> DATA
354 End data with <CR><LF>.<CR><LF>
> To: "Name" <email@email.com>
> Bcc: "Other Name" <other.email@email.com>
> From: "Name" <email@email.com>
> Date: ...
> Subject: Title
> lorem ipsum
>
> .
250 OK: queued as 79987
> QUIT
221 Bye
```

## Additional Security

As with many web protocols, SMTP was not designed with security in mind. Here we
will examine some additional methods for validating email authenticity and
prohibit email spoofing.

### SPF

SPF (Sender Policy Framework)

Has TXT record on the domain that might look like

```
v=spf1 -all
```

### DKIM

DKIM (Domain Keys Identified Mail) uses digital signatures where the public key
is distributed via a record on `selector._domainkey.example.com` (typically a
CNAME record).

### DMARC

DMARC is a policy for how email that fail either SPF or DKIM should be handled.
One can configure receiving mail server to send back reports on failed checks.

DMARC uses a TXT record at `_dmarc.example.com` TXT which might look like

```
"v=DMARC1; p=none"
```
