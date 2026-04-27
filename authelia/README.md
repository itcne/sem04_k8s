# Authelia

This directory contains the Kubernetes manifest for deploying Authelia using ArgoCD.

## Overview

Authelia is a single sign-on and multi-factor authentication portal for web apps. This application is managed by ArgoCD to ensure that the desired state defined in this repository matches the actual state in the Kubernetes cluster.

## Application Details

- **Name**: authelia
- **Namespace**: authelia
- **Chart**: authelia
- **Repository URL**: https://charts.authelia.com/
- **Target Revision**: 0.11.4

## Sync Policy

The sync policy is configured to create the namespace if it does not exist.

## Secrets

The secret must exist on the cluster before the application can be deployed, and it must contain all three keys used by the chart:

```bash
RESET_PASSWORD_HMAC_KEY="$(openssl rand -base64 64 | tr -d '\n')"
SESSION_ENCRYPTION_KEY="$(openssl rand -base64 64 | tr -d '\n')"
STORAGE_ENCRYPTION_KEY="$(openssl rand -base64 64 | tr -d '\n')"

kubectl create secret generic authelia-secrets \
  --from-literal="identity_validation.reset_password.jwt.hmac.key=${RESET_PASSWORD_HMAC_KEY}" \
  --from-literal="session.encryption.key=${SESSION_ENCRYPTION_KEY}" \
  --from-literal="storage.encryption.key=${STORAGE_ENCRYPTION_KEY}" \
  -n authelia
```

## Runtime

This deployment is intended to run as a single instance with `ReadWriteOnce` storage.
