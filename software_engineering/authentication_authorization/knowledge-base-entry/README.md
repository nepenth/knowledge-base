## Overview

OAuth 2.0: A Comprehensive Guide
=====================================

### Introduction

OAuth 2.0 is an authorization framework that enables secure access to resources without sharing passwords. It provides a standardized way for clients to request limited access to a resource on behalf of the resource owner. In this guide, we will delve into the main concepts of OAuth 2.0, including authorization code flow, tokens, and single sign-on (SSO).

### Authorization Code Flow

The authorization code flow is a widely used OAuth 2.0 flow that allows clients to request access to a protected resource without sharing their credentials. The flow involves the following steps:

1. **Client Registration**: The client registers with the authorization server and obtains a client ID.
2. **Authorization Request**: The client redirects the user to the authorization server's authorization endpoint, where the user grants or denies access.
3. **Authorization Code**: If the user grants access, the authorization server redirects the user back to the client with an authorization code.
4. **Token Request**: The client requests an access token from the authorization server by providing the authorization code.

**Example: Authorization Code Flow**
```http
# Step 1: Client Registration
POST /register HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

client_id=client123&client_secret=secret456

# Step 2: Authorization Request
GET /authorize?response_type=code&client_id=client123&redirect_uri=https://example.com/callback HTTP/1.1
Host: example.com

# Step 3: Authorization Code
HTTP/1.1 302 Found
Location: https://example.com/callback?code=auth_code_123

# Step 4: Token Request
POST /token HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&code=auth_code_123&redirect_uri=https://example.com/callback
```
### Authorization vs Authentication

OAuth 2.0 is often confused with authentication, but they serve different purposes:

* **Authorization**: OAuth grants access to a protected resource without sharing credentials.
* **Authentication**: OIDC (OpenID Connect) verifies the user's identity and provides an ID token.

**Example: OIDC Flow**
```http
# Step 1: Authentication Request
GET /authorize?response_type=code&client_id=client123&redirect_uri=https://example.com/callback&scope=openid HTTP/1.1
Host: example.com

# Step 2: ID Token
HTTP/1.1 302 Found
Location: https://example.com/callback?code=id_token_123

# Step 3: Token Request
POST /token HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&code=id_token_123&redirect_uri=https://example.com/callback
```
### Tokens

OAuth 2.0 uses two types of tokens:

* **Access Token**: Used to retrieve data from a protected resource.
* **Refresh Token**: Used to extend access to a protected resource without requiring the user to re-authenticate.

**Example: Access Token**
```http
# Step 1: Token Request
POST /token HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&code=auth_code_123&redirect_uri=https://example.com/callback

# Step 2: Protected Resource Request
GET /protected/resource HTTP/1.1
Host: example.com
Authorization: Bearer access_token_123
```
### Single Sign-On (SSO)

OAuth 2.0, OIDC, and SAML can be used to implement single sign-on (SSO) across multiple applications.

**Example: SSO Flow**
```http
# Step 1: User Authenticates
GET /login HTTP/1.1
Host: example.com

# Step 2: Authorization Server Redirects
HTTP/1.1 302 Found
Location: https://example.com/callback?code=sso_code_123

# Step 3: Client Requests Token
POST /token HTTP/1.1
Host: example.com
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code&code=sso_code_123&redirect_uri=https://example.com/callback
```
### Key Points and Takeaways

* OAuth 2.0 is an authorization framework that enables secure access to resources without sharing passwords.
* The authorization code flow is a widely used OAuth 2.0 flow that allows clients to request limited access to a protected resource.
* OIDC verifies the user's identity and provides an ID token.
* Access tokens are used to retrieve data from a protected resource, while refresh tokens extend access without requiring re-authentication.
* SSO can be implemented using OAuth 2.0, OIDC, or SAML.

### References

* [OAuth 2.0 Specification](https://tools.ietf.org/html/rfc6749)
* [OpenID Connect Specification](https://openid.net/specs/openid-connect-core-1_0.html)
* [SAML Specification](https://www.oasis-open.org/standards#samlv2.0)

## Key Takeaways

- To be updated.

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1870577916024868875)