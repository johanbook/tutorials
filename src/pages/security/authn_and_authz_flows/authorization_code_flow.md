# Authorization Code Flow

The Authorization Code Flow is an OAuth flow.

## Flow

This is how I understand the flow;

1. A client requests a resource from the resource server.
2. The resource server pings the authorization server. If OK the resource server
   proceeds otherwise client is redirected to an authorization prompt.
3. On confirmed prompt, the authorization server sends an authorization code to
   the resource server.
4. The resource server returns authorization code and resource server secret to
   authorization server.
5. Authorization server confirms authorization code and secret and answers with
   access code (and ID token in case of OIDC).
