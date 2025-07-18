# 🧪 OIDC Playground

A lightweight playground for simulating OpenID Connect (OIDC) flows and testing [Workload Identity Federation](https://cloud.google.com/iam/docs/workload-identity-federation) in Google Cloud. Ideal for testing federated identity scenarios in local or serverless environments.

This repo includes:

- [`mock-oidc-idp`](./mock-oidc-idp): A minimal OIDC identity provider that issues signed tokens for testing purposes.
- [`gcp-oidc-client`](./gcp-oidc-client): A Streamlit-based client for exploring token issuance and exchange with Google Cloud STS.

> See each subdirectory for setup and usage instructions.
