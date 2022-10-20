
Krateo PlatformOps is an open source tool, based on CNCF projects such as Kubernetes and Crossplane, that gives users the capability to create any desired resource on basically any infrastructure they'd like.

Therefore, Krateo PlatformOps introduces and uses the following terms.

### Module

A Krateo module is basically a [Crossplane Composition](https://github.com/crossplane/crossplane/blob/master/docs/concepts/composition.md) - it configures how Crossplane should compose resources into a higher level “composite resource”. 

> A Composition tells Crossplane “when someone creates composite resource X, you should respond by creating resources Y and Z”.

### Managed Resource

Managed resources are granular, high fidelity representations of a resource in an external system.

!!! Note
    Managed resources are what Crossplane enables platform teams to compose into higher level composite resources, forming an opinionated platform API. 
    
    They’re the building blocks of Crossplane.


### Provider

A Provider is a bundle set of [managed resources](#managed-resource) and their respective controllers to allow Crossplane to provision the respective infrastructure resource.

!!! Note

    A provider it’s a bundle set of managed resources and the related controllers deployed as Pod.

    It will install the CRDs for the resources it manages and watch on them. 
    
    Each instance of a managed resource will make the controller create and maintain a resource.

### Package

Packages extend Krateo, either with support for new kinds of modules, or support for new kinds of managed resources. There are two types of Krateo package; modules and providers.

