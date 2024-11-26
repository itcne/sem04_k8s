# Nginx Ingress Controller

This directory contains the Kubernetes manifest for deploying the Nginx Ingress Controller using ArgoCD.

## Overview

The Nginx Ingress Controller is an ingress controller that uses ConfigMap to store the nginx configuration. This application is managed by ArgoCD to ensure that the desired state defined in this repository matches the actual state in the Kubernetes cluster.

## Application Details

- **Name**: nginx-ingress
- **Namespace**: ingress-nginx
- **Chart**: ingress-nginx
- **Repository URL**: https://kubernetes.github.io/ingress-nginx
- **Target Revision**: 3.34.0

## Sync Policy

The sync policy is configured to create the namespace if it does not exist.
