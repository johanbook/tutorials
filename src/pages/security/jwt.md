# JSON Web Token

A JSON Web Token (JWT) is a JSON encoded in a string and contains a number of
claims. These tokens are signed and can be used to communicate authentication or
authorization. JWTS are url-safe as they are Base64 encoded.

## Structure

A JWT consists of three parts delimited by periods. It has a header, payload
(claims) and a signature. The header contains algorithm and token type. The
payload can be something like

```js
{
  sub: "my-user-id", // subject, can be e.g. user id
  name: "my-name", // custom claim
  iat: 14328 // issued at
}
```

## Security

Since a JWT is signed, any tampering with it will invalidate it. However, since
JWT are meant to be public they should contain no sensitive data. They should
typically be short-lived.
