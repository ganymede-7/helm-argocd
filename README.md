
# Argo CD Helm Chart Configuration

This README provides an overview of the Argo CD Helm chart configuration used for deploying Argo CD with ingress, persistence, and other enabled components.

## Server Configuration

- **Ingress Enabled**: Yes
- **Ingress Class Name**: `public`
- **Hostname**: `argocd.local`
- **Path**: `/`
- **Path Type**: `ImplementationSpecific`
- **Annotations**:
  - `nginx.ingress.kubernetes.io/ssl-redirect`: `"false"`
  - `nginx.ingress.kubernetes.io/rewrite-target`: `/`
  - `nginx.ingress.kubernetes.io/backend-protocol`: `"HTTP"`
- **Extra Arguments**:
  - `--insecure`
- **GRPC Ingress Enabled**: No

## Configurations

- **Server Insecure Mode**: Enabled (`server.insecure: true`)

## ApplicationSet

- **Enabled**: Yes

## Controller

- **Replicas**: 1
- **Persistence**:
  - **Enabled**: Yes
  - **Size**: `2Gi`
  - **Storage Class Name**: `microk8s-hostpath`

## Redis

- **Enabled**: Yes
- **Persistence**:
  - **Enabled**: Yes
  - **Size**: `2Gi`
  - **Storage Class Name**: `microk8s-hostpath`

## Dex

- **Enabled**: Yes

## Repo Server

- **Persistence**:
  - **Enabled**: Yes
  - **Size**: `2Gi`
  - **Storage Class Name**: `microk8s-hostpath`

## Notes

- This configuration is tailored for a MicroK8s environment using the `microk8s-hostpath` storage class.
- Insecure mode is enabled for development or internal use cases.
- Ingress is configured for HTTP access without SSL redirection.

