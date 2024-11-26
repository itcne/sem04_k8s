# Cert-Manager

This directory also contains the Kubernetes manifest for deploying Cert-Manager using ArgoCD.

## Overview

Cert-Manager is a Kubernetes add-on to automate the management and issuance of TLS certificates from various issuing sources. This application is managed by ArgoCD to ensure that the desired state defined in this repository matches the actual state in the Kubernetes cluster.

## Application Details

- **Name**: cert-manager
- **Namespace**: cert-manager
- **Chart**: cert-manager
- **Repository URL**: https://charts.jetstack.io
- **Target Revision**: v1.5.3

## Sync Policy

The sync policy is configured to create the namespace if it does not exist.
