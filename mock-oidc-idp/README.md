# 🪪 Mock OpenID Connect (OIDC) Identity Provider

A lightweight OpenD Connect (OIDC) Identity Provider (IdP) that issues signed ID tokens using a configurable RSA private key. Useful for simulating federated identity scenarios, such as testing [Workload Identity Federation (WIF)](https://cloud.google.com/iam/docs/workload-identity-federation) in Google Cloud without relying on a full-fledged OIDC provider. Read [this](https://alphasec.io/secure-federated-access-to-google-cloud-building-a-mock-oidc-identity-provider/) blog post for more information.


### ✨ Features

- Serves [OIDC discovery metadata](https://openid.net/specs/openid-connect-discovery-1_0.html)
- Provides a JWKS endpoint for token verification
- Issues signed ID and access tokens via `/token`
- Customizable subject `sub` and `email` via query params or JSON payload
- Minimal dependencies and deployable anywhere, including [Cloud Run](https://cloud.google.com/run?hl=en), [Railway](https://railway.app/?referralCode=alphasec), or [DigitalOcean](https://m.do.co/c/5552e11c260f).


### 🔧 Environment Variables

| Variable          | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
| `PRIVATE_KEY_PEM` | The RSA private key in PEM format, used to sign tokens                                           |
| `ISSUER_URL`      | The OIDC issuer URL (must match what clients expect in `iss`)                                    |
| `CLIENT_ID`       | The audience (`aud`) claim of ID token, indicates which app is requesting authentication         |
| `AUDIENCE`        | The audience (`aud`) claim of access token, tells the API (resource server) who the token is for |
| `KEY_ID`          | The key ID (`kid`) used in JWT headers and JWKS metadata                                         |


### 🧪 Endpoints

| Path                                        | Description                              |
|---------------------------------------------|------------------------------------------|
| `/`                                         | Health check                             |
| `/.well-known/openid-configuration`         | Returns the OIDC discovery document      |
| `/.well-known/jwks.json`                    | Returns the JWKS public key set          |
| `/token`                                    | Returns signed ID and access tokens      |
| `/authorize`                                | Stub endpoint (501 Not Implemented)      |


### 🔒 Security Considerations
Important: This is a mock identity provider and not intended for production use. It uses static keys and no request validation for simplicity. Use only in trusted test environments.
