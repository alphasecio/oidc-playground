# 🛠️ OIDC Client Playground

A simple OpenID Connect (OIDC) client built with Streamlit. Built to work alongside the [mock OIDC IdP](https://github.com/alphasecio/oidc-playground/blob/main/mock-oidc-idp/README.md) and test [Workload Identity Federation](https://cloud.google.com/iam/docs/workload-identity-federation) with Google Cloud. Can easily be deployed to serverless platforms like [Railway](https://railway.app/?referralCode=alphasec), [Cloud Run](https://cloud.google.com/run?hl=en), and others. Read [this](https://alphasec.io/secure-federated-access-to-google-cloud-simulating-access-with-a-headless-oidc-client) blog post for more information.

## ✨ Features

1. **Get OpenID Configuration** (`/.well-known/openid-configuration`)
2. **Get JWKS** (`/.well-known/jwks.json`)
3. **Generate ID Token** via `POST /token`, with `sub` and `email` claims
4. **Exchange ID Token with Google Cloud STS** and receive a federated token
5. **Impersonate Service Account** using federated token
6. **List GCS Buckets** using service account access token


## 🧰 Running the Client

* Ensure the mock OIDC IdP is running
* Install the requirements: `pip install -r requirements.txt`
* Run the server: `streamlit run app.py`
* The server starts at: `http://localhost:8501`
* Alternatively, use the provided `Dockerfile`.

## 🧠 Usage Overview
#### 🔍 Get OpenID Config / JWKS
- Choose the action → click Submit → view JSON.

#### 🔑 Generate ID Token
- Fill Subject, optionally Email → Submit → view raw and decoded ID and access tokens.

#### 🔄 Exchange with STS
- Paste ID token and STS Audience → Submit → get federated token from STS.

#### 👤 Impersonate Service Account
- Paste federated token + service account email → Submit → get service account access token.

#### 📦 List GCS Buckets
- Provide service account token + GCP project ID → Submit → list buckets.
