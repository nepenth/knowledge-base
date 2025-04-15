## Overview
OAuth 2.0 is an authorization framework that enables applications to obtain limited access to user accounts on HTTP services. It works by delegating user authentication to the service that hosts the user account and authorizing third-party applications to access that account.

## Key Components

### Authorization Code Flow
This flow is used for server-side applications where the client can securely store a client secret. The basic steps are:

```python
# Example of Authorization Code Flow using Python requests library

import requests

def get_authorization_code():
    auth_url = "https://authorization-server.com/auth"
    params = {
        'client_id': 'your_client_id',
        'response_type': 'code',
        'redirect_uri': 'your_redirect_uri'
    }
    return requests.get(auth_url, params=params)

def exchange_code_for_token(code):
    token_url = "https://authorization-server.com/token"
    data = {
        'grant_type': 'authorization_code',
        'code': code,
        'client_id': 'your_client_id',
        'client_secret': 'your_client_secret',
        'redirect_uri': 'your_redirect_uri'
    }
    return requests.post(token_url, data=data)
```

### Authorization vs Authentication
- **Authorization**: Determining what permissions an authenticated user has.
- **Authentication**: Verifying the identity of a user.

#### OAuth (Authorization)
```javascript
// Example OAuth authorization request
const authRequest = {
  client_id: 'client123',
  redirect_uri: 'https://example.com/callback',
  response_type: 'code',
  scope: 'read_profile'
};
```

#### OpenID Connect (OIDC) (Authentication)
```javascript
// Example OIDC authentication request
const authRequest = {
  client_id: 'client123',
  redirect_uri: 'https://example.com/callback',
  response_type: 'id_token code',
  scope: 'openid profile email'
};
```

### Tokens

#### Access Token
Used to access protected resources:
```python
# Using an access token to make a request
headers = {
    'Authorization': f'Bearer {access_token}'
}
response = requests.get('https://api.example.com/data', headers=headers)
```

#### Refresh Token
Used to obtain new access tokens when the current one expires:
```python
def refresh_access_token(refresh_token):
    token_url = "https://authorization-server.com/token"
    data = {
        'grant_type': 'refresh_token',
        'refresh_token': refresh_token,
        'client_id': 'your_client_id',
        'client_secret': 'your_client_secret'
    }
    return requests.post(token_url, data=data)
```

### Single Sign-On (SSO)

#### OAuth SSO
```javascript
// Example OAuth SSO configuration
const oauthConfig = {
  clientId: 'sso-client-id',
  scope: ['openid', 'profile'],
  redirectUri: 'https://example.com/sso/callback'
};
```

## Key Points and Takeaways

1. **Security**:
   - Never store client secrets in client-side code
   - Always use HTTPS for token exchange
   - Validate all tokens before using them

2. **Best Practices**:
   - Use appropriate scopes to limit access
   - Implement proper error handling
   - Store refresh tokens securely

3. **Common Flows**:
   - Authorization Code Flow (most common)
   - Implicit Flow (legacy, not recommended)
   - Client Credentials Flow (server-to-server)

4. **Token Management**:
   - Access tokens are typically short-lived
   - Refresh tokens should be used to obtain new access tokens
   - Implement token revocation when necessary

## References

1. [OAuth 2.0 Specification](https://oauth.net/2/)
2. [OpenID Connect Specification](https://openid.net/specs/openid-connect-core-1_0.html)
3. [RFC 6749 - The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)

## Additional Resources

- [OAuth 2.0 Playground](https://www.oauth.com/playground/)
- [OIDC Documentation](https://openid.net/connect/)
- [Security Considerations for OAuth 2.0](https://oauth.net/security/)

This knowledge base entry provides a comprehensive overview of OAuth 2.0, including practical examples and best practices. Remember to always follow security guidelines when implementing OAuth in your applications.

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1870577916024868875)