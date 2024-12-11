# Nextcloud - INT

This directory also contains the Kubernetes manifest for deploying Nextcloud using ArgoCD.

## Overview

Nextcloud is a suite of client-server software for creating and using file hosting services. This application is managed by ArgoCD to ensure that the desired state defined in this repository matches the actual state in the Kubernetes cluster.

## Application Details

- **Name**: nextcloud-int
- **Namespace**: s-nextcloud-int
- **Chart**: nextcloud
- **Repository URL**: https://nextcloud.github.io/helm/
- **Target Revision**: 6.2.4

## Sync Policy

The sync policy is configured to create the namespace if it does not exist.

## Secrets

The secrets must persist on the cluster before the application can be deployed:

```bash
kubectl create secret generic nextcloud-secret \
  --from-literal=nextcloud-admin-username=admin \
  --from-literal=nextcloud-admin-password=$(openssl rand -base64 32) \
  -n s-nextcloud-int
```
