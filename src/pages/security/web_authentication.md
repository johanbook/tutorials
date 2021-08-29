# Web Authentication

In this document, I will discuss authentication approaches for a system based on
HTTP that is to be accessed from a web browser.

## Cookies vs Tokens

To secure the system, each request must contain sufficient information to be
validated. That information can live either in the HTTP headers (or cookies) or
in its body. Of these options using the HTTP headers / cookies are the most
common so let us dissect their impact.

### Cookies

Cookies suit well for authentication due how browsers treat them. Using
domain-wide cookies one can achieve a SSO. However, it has the following
drawbacks:

- Requires cookies to be allowed in browser
- [XSRF attacks](threats/csrf.md)

### Tokens

One can instead of cookies use a token which is inserted into request headers.
However, this required running JavaScript/PHP and that being allowed in the
browser and inserts the token into the headers of each request.

A problem is where the token should be stored if one aims to achieve SSO.
Storing data in any web storage is as of now susceptible to [XSS](threats/xss).

## Stateless vs Stateful

One can either use a stateless approach (client has all information needed for
validation) or a stateful approach where the system creates a session and gives
the client a session id (SID).

If using a session-based approach, one can store IP and confirm that it matches.
Session can also be revoked. However it is very important that the SID is
generated **with high entropy**, otherwise it can be cracked.

If running multiple servers, one will need a sticky session (or a dedicated
authentication server / database tables).
