# Clams Demo OpenShift GitOps Manifest

GitOps manifest for an Clams Demo Platform built on OpenShift

## Providing an OpenShift Instance

There are many ways to provision OpenShift. For a convenient local instance, consider [OpenShift Local](https://access.redhat.com/documentation/en-us/red_hat_codeready_containers/2.0/html/getting_started_guide/installation_gsg).

## Bootstrapping

1. If you are not reusing an existing ArgoCD instance, provision OpenShift GitOps:

   `oc apply -k argocd/bootstrap`

1. Edit `argocd/platform-root.yaml` and customize the configuration (see [Configuration Guide](#configuration-guide)).

1. Provision the root ArgoCD Application:

   `oc apply -f argocd/platform-root.yaml`

## Configuration Guide

Below are the critical configuration parameters that require user-provided values.

### Clams Source

The Git coordinates for the Clams application

Example:

```yaml
  source:
    ...
    helm:
      parameters:
        - name: gitRepositoryUrl
          value: https://github.com/your-profile/App.git
        - name: gitRef
          value: your-feature
```