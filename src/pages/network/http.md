# HTTP

HTTP (Hyper Text Transport Protocol) is a network protocol for transferring
hypertext over [TCP](tcp). Hypertext itself is text containing hyperlinks, or
simply links, that link to other content, typically using the URI scheme. The
protocol is both stateless and response-request based. All responses and
requests are encoded in the TCP body. An HTTP connection is established on top
of TCP and an HTTP status code is received, e.g. `HTTP/1.1 200 OK`. HTTP itself
is a stateless protocol (which suits well with REST).

An example request can look like this

```
GET /
HTTP/1.1
Host: www.example.com
```

which could obtain the following response

```
HTTP/1.1 200 OK
Date: Mon, 23 May 2005 22:38:34 GMT
Content-Type: text/html;
charset=UTF-8
Content-Length: 155
Last-Modified: Wed, 08 Jan 2003 23:11:55
GMTServer: Apache/1.3.3.7 (Unix) (Red-Hat/Linux)
ETag:"3f80f-1b6-3e1cb03b"
Accept-Ranges: bytes
Connection: close

<html>
  <head>
    <title>An Example Page</title>
  </head>
  <body>
    <p>
      Hello World, this is a very simple HTML document.
    </p>
  </body>
</html>
```

The HTML content are typically gzipped.

## Methods

HTTP used different _verbs_ for request purpose. The allowed verbs are:

- **CONNECT** Used to establish a connection.
- **DELETE** Delete a resource.
- **GET** Get a resource.
- **HEAD** Get resource headers only. Useful to e.g. validate a cached resource.
- **OPTIONS** Checks what HTTP verbs a server supports, what CORS policy it has,
  etc. Used in preflighted requests.
- **PATCH** Modify a resource.
- **POST** Create a resource.
- **PUT** Replace a resource.
- **TRACE** Returns incoming request as response body. Useful for debugging but
  might allowing this method might introduce security vulnerabilities.

## HTTPS

HTTPS is an encrypted variant of HTTP using TLS (not there is also mTLS for
mutual authentication).

### TLS

TLS is the encryption protocol (that succeeds SSL).

#### TLS Handshake

When client establishes connection to server, the server responds with its SSL
certificate containing its public key. Client generates premaster secret
encrypted with the server's public key and sends to server. Both client and
server can then generate the same symmetric key, which will be used during the
session.

The SSL certificates are issued by a Certificate Authority (CA) and can verify
that the public key is authentic.

### SSL Termination

SSL termination is the point where HTTPS is decrypted to HTTP.

## Encodings

There are a few different common types of content encodings in HTTP (MIMEs). The
content type is specified in the `Content-Type` header.

### Form URL Encoding

If the body is encoded in same format as URL query parameters, the content type
`application/x-www-form-urlencoded` is used. It can look like

```sh
username=janice&password=84hf32khcckk
```

It is the default format used by HTML forms (unless binary data is supplied).
Unless coding in pure HTML, I discourage using this encoding in preference of
JSON.

### JSON

A lot of data transfer over HTTP is in the form of JSON, which has the MIME
`application/json`. A JSON body could look like

```json
{ "body": "cat" }
```

### Multipart Form Data

The multipart format, aka `multipart/form-data` is used for binary data. It uses
a boundary which **must not** appear naturally in the transmitted data. It can
look like this

```
...
content-type: multipart/form-data; boundary=----WebKitFormBoundaryjxASSSgNGXHs9JPt

------WebKitFormBoundaryjxASSSgNGXHs9JPt
Content-Disposition: form-data; name="text"

heyho where we go
------WebKitFormBoundaryjxASSSgNGXHs9JPt
Content-Disposition: form-data; name="more-text"

ein zwei drai
------WebKitFormBoundaryjxASSSgNGXHs9JPt--
```

Each boundary separated section starts with headers on its own, where
`Content-Disposition` states e.g. field name.

## CORS

Cross Origins Resource Sharing (CORS) is a policy that cross origin requests are
blocked by the web browser unless the server explicitly allows the origin in a
`Access-Control-Allow Origin` header. This is a security feature as the browser
can not trust that requests from scripts are intended by the user (and many such
requests would also by authenticated due to cookie being sent along with the
request).

A server can allow CORS from all origins by adding this header to its responses:

```
Access-Control-Allow-Origin: *
```
