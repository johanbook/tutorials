# URL

A Uniform Resource Locator (URL) is an address to some resource. It also
includes information on how that resource should be accessed (via its protocol).

Consider the URL `http://localhost:8080/alpha?bravo=charlie#delta`. It consists
of several parts;

- **schema** (`http`), also known as protocol. It specifies how the resource
  should be accessed.
- **host** (`localhost`), also known as hostname. In terms of DNS, this
  corresponds to the domain.
- **port** (`8080`), the port (if any) the resource can be found at.
- **path** (`/alpha`)
- **query** (`?bravo=charlie`) is key-value pairs data. There is not agreed on
  standard on how exactly the data should be represented (especially for nested
  values).
- **fragment** (`#delta`)

There are some additional terms

- **netloc** (`localhost:8080`), the hostname and port. This is also sometimes
  sloppily called host. Can also be called authority.
