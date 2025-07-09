# 🪪 Mock OpenID Connect (OIDC) Identity Provider

A lightweight OpenD Connect (OIDC) Identity Provider (IdP) that issues signed ID tokens using a configurable RSA private key. Useful for simulating federated identity scenarios, such as testing [Workload Identity Federation (WIF)](https://cloud.google.com/iam/docs/workload-identity-federation) in Google Cloud without relying on a full-fledged OIDC provider. Read [this](https://alphasec.io/secure-federated-access-to-google-cloud-building-a-mock-oidc-identity-provider/) blog post for more information.


### ✨ Features

- Serves [OIDC discovery metadata](https://openid.net/specs/openid-connect-discovery-1_0.html)
- Provides a JWKS endpoint for token verification
- Issues signed ID tokens via `/generate-token`
- Customizable subject (`sub`), email, and roles via query params or JSON payload
- Minimal dependencies and deployable anywhere, including [Cloud Run](https://cloud.google.com/run?hl=en), [Railway](https://railway.app/?referralCode=alphasec), or [DigitalOcean](https://m.do.co/c/5552e11c260f).


### 🔧 Environment Variables

| Variable          | Description                               |
|-------------------|-------------------------------------------|
| `PRIVATE_KEY_PEM` | RSA private key (PEM format, single-line) |
| `ISSUER_URL`      | Base URL of this IdP (e.g. `https://...`) |
| `AUDIENCE`        | Audience claim (`aud`) for tokens         |
| `KEY_ID`          | `kid` value in JWT and JWKS headers       |


### 🧪 Endpoints

| Path                                        | Description                           |
|---------------------------------------------|---------------------------------------|
| `/`                                         | Health check                          |
| `/.well-known/openid-configuration`         | OIDC discovery document               |
| `/jwks.json`                                | JWKS public key set                   |
| `/generate-token`                           | Returns a signed OIDC ID token        |
| `/authorize`                                | Stub endpoint (501 Not Implemented)   |


### 🔒 Security Considerations
Important: This is a mock identity provider and not intended for production use. It uses static keys and no request validation for simplicity. Use only in trusted test environments.
