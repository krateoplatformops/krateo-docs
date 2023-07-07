# Definition of Krateo Operator

* Owner: Luca Sepe (@lucasepe)
* Reviewers: Krateo Maintainers
* Status: Draft, revision 0.1

## Goals

Scope of this definition is to design the specification for the Krateo operator and what we expect from its controller.

With the Krateo operator implementation we want to let Krateo be installed with a gitops approach and the related lifecycle management.

We want as well to provide an additional operator that can be added to https://operatorhub.io/, meaning that every OpenShift cluster will be able to use it. 

If another Kubernetes distribution is available, then there will be another - but consistent - version of the operator.

## Krateo Operator Manifest

Krateo Operator will handle a kubernetes custom resource (manifest) in order to bootstrap the Krateo Runtime. 

```yaml
apiVersion: krateo.io/v1alpha1
kind: Runtime
metadata:
  name: krateo-runtime
  namespace: krateo-system
spec:
  crossplaneVersion: v1.10 # if not specified install latest version
  crdsVersion: 0.3.7 # if not specified install latest version
  extraEnvVars:
    httpProxy: # hostname or IP address of your proxy server
    httpsProxy: # hostname or IP address of your proxy server
    noProxy: # list of destination domain names, domains, IP addresses or other network CIDRs to exclude proxying
```

## Krateo Operator Controller

The Krateo operator controller using the namespace defined in the related `Runtime` resource will do the following:

- install crossplane
- install crossplane provider helm
- install crossplane provider kubernetes
- create cluster role bindings


