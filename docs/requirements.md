# Requirements

To correctly install Krateo PlatformOps fulfill the following requirements:

- [CNCF Certified Kubernetes cluster](https://landscape.cncf.io/card-mode?category=platform&grouping=category)

- Kubernetes minimal requirements:
  * 3 workers, each with 2vCPUs and 4GiB RAM – no storage required
  * Ability to expose service of type LoadBalancer (https://kubernetes.io/docs/tasks/access-application-cluster/create-external-load-balancer/)

- Networking requirements
  * Ability to reach https://github.com , https://charts.krateo.io , https://charts.konghq.com , xpkg.upbound.io , ghcr.io, docker.io

If you meet this requirement, you can proceed with the [installation](./cli/cli-overview.md#installing-the-krateo-cli).
