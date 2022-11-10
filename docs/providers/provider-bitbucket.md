# Provider Bitbucket

## Overview

This is a Kubernetes Operator (Crossplane provider) that:

- create and delete Bitbucket repositories
- manage Bitbucket user permissions

## Getting Started

With Crossplane installed in your cluster:

```sh
$ helm repo add crossplane-stable https://charts.crossplane.io/stable
$ helm repo update
$ helm install crossplane --namespace crossplane-system crossplane-stable/crossplane
```

### Install this provider

Install the below manifest:

```sh
cat <<EOF | kubectl apply -f -
apiVersion: pkg.crossplane.io/v1
kind: Provider
metadata:
  name: crossplane-provider-bitbucket
spec:
  package: 'ghcr.io/krateoplatformops/provider-bitbucket:VERSION'
  packagePullPolicy: IfNotPresent
EOF
```

!!! note ""

   replace `VERSION` with [latest provider tag](https://github.com/krateoplatformops/provider-bitbucket/tags)

### Configure the provider

```sh
cat <<EOF | kubectl apply -f -
apiVersion: bitbucket.krateo.io/v1alpha1
kind: ProviderConfig
metadata:
  name: bitbucket-provider-config
spec:
  apiUrl: http://10.99.99.37:7990
  verbose: true
  insecure: true
  credentials:
    source: Secret
    secretRef:
      namespace: default
      name: bitbucket-secret
      key: token
EOF
```

### Configuring the `Repo` custom resource

```sh
cat <<EOF | kubectl apply -f -
apiVersion: bitbucket.krateo.io/v1alpha1
kind: Repo
metadata:
  name: bitbucket-provider-example
spec:
  forProvider:
    project: JXP
    name: demo-repo
    private: true
  providerConfigRef:
    name: bitbucket-provider-config
EOF
```

### Configuring the `RepoPermissionUser` custom resource

```sh
cat <<EOF | kubectl apply -f -
apiVersion: bitbucket.krateo.io/v1alpha1
kind: Repo
metadata:
  name: bitbucket-provider-example
spec:
  forProvider:
    project: JXP
    name: demo-repo
    private: true
  providerConfigRef:
    name: bitbucket-provider-config
EOF
```
