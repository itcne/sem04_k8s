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

The secrets must exist on the cluster before the application can be deployed:

```bash
kubectl create secret generic authelia-secrets \
  --from-literal='session.encryption.key='"$(openssl rand -base64 64 | tr -d '\n')" \
  --from-literal='storage.encryption.key='"$(openssl rand -base64 64 | tr -d '\n')" \
  -n authelia
```
