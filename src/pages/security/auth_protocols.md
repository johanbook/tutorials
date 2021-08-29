# Authentication and Authorization Standards

In this document we will look into some different standards for authentication
and authorization. Note that OpenID and OAuth are protocols for letting a third
party access your resources.

First let's introduce some terminology:

- **Single Sign-On** A process where a user signs in once to access all services
  in a system. The user should not need to enter credentials again. Can be
  implemented with domain-wide cookies (assuming the whole system is contained
  to a single domain).

## SAML

Security Assertion Markup Language (SAML) is an **authentication and
authorization** standard. In SAML there are

- **User Agent (UA)** Typically the user's web browser.
- **Service Provider (SP)** The service that we want to access.
- **Identity Provider (IDP)** The service that federates identities.

The service provider must trust the identity provider.

When the UA interacts with the IDP it creates a SAML assertion which is sent to
the UA which in turn sends it to the SP.

The configurations often reside in an XML file.

SAML was not initially designed for the web and has been retrofitted for it
afterwards. It is also quite verbose.

## OAuth

OAuth is an **authorization protocol** where the authorization is provided by an
**identity provider**. This alleviates the client site from storing any user
passwords. It also constitutes the magic behind social logins.

To better understand OAuth, we will introduce some core terminology.

- **Client** A service that wants to access the resource server on behalf of a
  user.
- **Resource server** The owner of the desired resource.
- **Authorization server** Authorizes the client to access the resource server.

To accomplish this, two kinds of tokens are introduced;

- **Access token** A token specifying authorization for a user, but does not
  contain identifying information. It declares what scopes can be accessed.
  Access tokens are typically meant to be understood by resource server only.
- **Refresh token** A token used for obtaining an access token.

## OpenID

OpenID is an **authentication protocol** that uses an identity provider.

### OpenID Connect

Since, OAuth does not support authentication, OpenID Connect (OIDC) was
introduced. It is built on top of OAuth.

OIDC introduces the concept of an ID token, which is a [JWT](jwt) token
identifying a user. Possessing an ID token is proof of authentication, which
does not apply for an access token since those can be obtained in multiple ways.
In contrast to an access token, the id token is meant to be understood by the
client.

As of 2021, the recommendation is to use Proof Key for Code Exchange (PKCE).
