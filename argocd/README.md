## ArgoCD Ingress

The Ingress resource for ArgoCD is configured to expose the ArgoCD server to external traffic. This allows users to access the ArgoCD web UI and API from outside the Kubernetes cluster.

> This only deploys the configuration for the ingress. The ArgoCD is installed in the base-setup

### Ingress Details

- **Name**: argocd-server-ingress
- **Namespace**: argocd
- **TLS**: Enabled with a certificate managed by Cert-Manager
