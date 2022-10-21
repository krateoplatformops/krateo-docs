To install Krateo PlatformOps on your cluster all you need is the [Krateo CLI](cli/cli-overview.md) tool.

You can install [Krateo CLI](cli/cli-overview.md) tool for your favorite OS, follow [these instructions](cli/cli-install.md).

With [Krateo CLI](cli/cli-overview.md) tool ready to go, open a terminal and type this command:

```sh
krateo init
```

!!! note

    If you want to see what `krateo init`command does, you can look at [it's sequence diagram](cli/cli-init-workflow.md).

you will see something like this:

```sh
[done] √ crossplane 1.10.0 installed               
[wait] ⢎⠁ installing package provider-helm (v0.12.0)... (6s)
```

Once the core components are installed, you will be asked to specify the domain where the dashboard will be reachable.

```sh
[done] √ crossplane 1.10.0 installed               
[done] √ package provider-helm (v0.12.0) installed               
[done] √ package provider-kubernetes (v0.5.0) installed               
[done] √ package provider-git (v1.2.0) installed               
[done] √ package provider-argocd-token (v1.3.0) installed               
[done] √ role bindings 'provider-helm-admin-binding' created                 
[done] √ role bindings 'provider-kubernetes-admin-binding' created                 
[done] √ core module installed            
 > domain :           
```

Type your domain (i.e. krateo.site) and hit the :leftwards_arrow_with_hook: key.

```sh
[done] √ crossplane 1.10.0 installed               
[done] √ package provider-helm (v0.12.0) installed               
[done] √ package provider-kubernetes (v0.5.0) installed               
[done] √ package provider-git (v1.2.0) installed               
[done] √ package provider-argocd-token (v1.3.0) installed               
[done] √ role bindings 'provider-helm-admin-binding' created                 
[done] √ role bindings 'provider-kubernetes-admin-binding' created                 
[done] √ core module installed            
 > domain : krateo.site
[done] √ core module claims installed                
[wait] ⠈⡱ waiting for Krateo readiness ... (10s)
```

After a while the CLI tool will print the full URI to your Krateo PlatformOps dashboard. 