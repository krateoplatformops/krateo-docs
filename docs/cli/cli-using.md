# Using the Krateo CLI

For configuration, krateo looks for a file named config in the `$HOME/.kube` directory. 

You can specify other kubeconfig files by setting the `KUBECONFIG` environment variable or by setting the `--kubeconfig` flag.

This overview covers krateo syntax, describes the command operations, and provides common examples.

## Syntax

Use the following syntax to run krateo commands from your terminal window:

```sh
krateo [command] [flags]
```

where command and flags are:

- command: Specifies the operation that you want to perform, for example `init`, `uninstall`
- flags: Specifies optional flags. For example, you can use the `-v` or `--verbose` flags to output verbose info while executing the command

If you need help, run `krateo help` from the terminal window.


## Operations

The following table includes short descriptions and the general syntax for all of the krateo operations:

| Operation   | Syntax                                      | Description                                          |
|:------------|:--------------------------------------------|:-----------------------------------------------------|
| init        | [krateo init](#krateo-init-flags)           | Initialize your cluster with the Krateo PlatformOps  |
| uninstall   | [krateo uninstall](#krateo-uninstall-flags) | Uninstall Krateo PlatformOps from your cluster       |
| version     | krateo version                              | Print the Krateo CLI tool version and build info     |
| help        | krateo [command] help                       | Print more information about a command               |

### `krateo init [flags]`

Scope: Initialize your cluster with the Krateo PlatformOps

| Flag                    | Default value      | Description                                    |
|:------------------------|:-------------------|:-----------------------------------------------|
| --context <string>      |                    | specify the kubeconfig context to use          |
| --help                  |                    | print the help for this krateo init command    |
| --http-proxy <string>   | HTTP_PROXY env var | use the specified HTTP proxy                   |
| --https-proxy <string>  | HTTPS_PROXY env var| use the specified HTTPS proxy                  |
| --kubeconfig <string>   | $HOME/.kube/config | absolute path to the kubeconfig file           |
| --namespace <string>    | krateo-system      | namespace where to install Krateo PlatformOps  |
| --no-proxy <string>     | NO_PROXY env var   | comma-separated list of hosts and domains<br/>which do not use the proxy |
| --openshift             |                    | specify this if installing Krateo PlatformOps on OpenShift |
| --verbose               |                    | print verbose information                      |

### `krateo uninstall [flags]`

Scope: Uninstall Krateo Platform Ops from your cluster

| Flag                    | Default value      | Description                                    |
|:------------------------|:-------------------|:-----------------------------------------------|
| --context <string>      |                    | specify the kubeconfig context to use          |
| --dry-run               |                    | preview the object that would be deleted,<br/>without really deleting it
| --help                  |                    | print the help for this krateo init command     |
| --kubeconfig <string>   | $HOME/.kube/config | absolute path to the kubeconfig file            |
| --namespace <string>    | krateo-system      | namespace where Krateo PlatformOps is installed |
| --verbose               |                    | print verbose information                       |
