# Definition of Krateo Module, Template and Deployment

* Owner: Diego Braga (@braghettos)
* Reviewers: Krateo Maintainers
* Status: Draft, revision 1.0

## Background

In order to build a strategic design for Krateo, we need to define our [*Ubiquitous Language*](https://martinfowler.com/bliki/UbiquitousLanguage.html).

> Ubiquitous Language is the term Eric Evans uses in Domain Driven Design for the practice of building up a common, rigorous language between developers and users. This language should be based on the Domain Model used in the software - hence the need for it to be rigorous, since software doesn't cope well with ambiguity.

> Evans makes clear that using the ubiquitous language in conversations with domain experts is an important part of testing it, and hence the domain model. He also stresses that the language (and model) should evolve as the team's understanding of the domain grows.

The language we develop together through collaboration will become ubiquitous, pervasive, throughout the team’s spoken
communication and software model.

A ubiquitous language is a vocabulary shared by everyone involved in a project, from domain experts to stakeholders, to project managers, to developers. This language should be used in all documentation, tickets, conversations, meeting invites, post-it notes on your computer, chalkboards that only appear in your dreams — everywhere. The goal is to reduce the ambiguity of communication.

> Bounded Context is a central pattern in Domain-Driven Design. It is the focus of DDD's strategic design section which is all about dealing with large models and teams. DDD deals with large models by dividing them into different Bounded Contexts and being explicit about their interrelationships.

DDD is about designing software based on models of the underlying domain. DDD deals with large models by dividing them into different Bounded Contexts and being explicit about their interrelationships.

I really like Alberto Brandolini's article [*About Bounded Contexts and Microservices*](https://blog.avanscoperta.it/2020/06/11/about-bounded-contexts-and-microservices/) expecially when it comes to the comparison between a Bounded Context and a microservice. We will follow these suggestions to translate our Bounded Contexts to microservices.

## Goals

Benefits of having a ubiquitous language are basically three:
1. Clearer communication. Less ambiguity. It makes it less likely to have misunderstanding and mismatched expectations.
2. A useful shorthand can develop. Once the ubiquitous language becomes more ingrained, and good habits are established, an enormous amount of information and context is communicated when someone uses the word "Template"
3. People involved become more aware of potential issues when they come up, creating a beneficial feedback loop. Developers can push back against terms that are ambiguous or inconsistent. Stakeholders have an extra leg to stand on to insist that developers use terms that they can understand or ask questions about words that seem too awkward to use in everyday conversation. This leads to more back and forth communication that strengthens the shared language and makes it more relevant for everyone.

This one pager is the evolution of proposal https://github.com/krateoplatformops/krateo-docs/issues/2.

## Proposal

Krateo will follow the Bounded Context approach, starting with three definitions: Krateo Module, Krateo Template and Krateo Deployment.

### Krateo Module

A self-consistent set of components that allows Krateo to deliver new functionalities. *Functionality* means a feature with a specific goal for the final user like the Krateo UI (composition of frontend/backend) or a classic backend service (e.g. to collect metrics or events).

This set of components is made up of packaged streams of YAML manifests that represents the resources that will be applied.
A module doesn't require inputs from the UI via form (aka [Krateo Template](#krateo-template)).

#### Krateo Module deep dive into technical definition

An example of a Krateo Module can be *krateo-module-ui*, which will contain the frontend, different microservice backends and other components like the [Eventrouter](https://github.com/krateoplatformops/eventrouter). Another example can be *krateo-module-argocd*, which will contain ArgoCD helm chart or operator for Openshift, *argocd-api* (to return plain data) and *argocd-app* (to convert plain data for the frontend).

*An helm chart should install only one tool as it represents the packaging for microservice manifests.* This means that an Helm chart is not a feasible way to package a Krateo Module.

A Krateo Module is represented by a [Crossplane claim](https://docs.crossplane.io/v1.10/concepts/composition/#claiming-composite-resources) and is packaged via OCI image.

When a Krateo Module manifest is applied to the Kubernetes cluster, the related [Configuration Package](https://docs.crossplane.io/v1.10/concepts/packages/#configuration-packages) is applied and then a claim is generated from the Krateo Module specs and applied.

*It is not possible to use a pre-defined claim because it cannot be packaged via OCI image. This means that every spec for the claim must be specified in the Module specs.*

More details in a related issue.

### Krateo Template

A form that guides users via Krateo UI to build specifications for a [Krateo Deployment](#krateo-deployment).
Krateo Template resources have the same user experience and is represented by a YAML manifest that describes which widgets and graphical element should be rendered.

Krateo Template lets Platform Engineers to choose the best way to ask for user inputs, like providing widgets, default values, a well-defined list of choices, regex to validate user input etc.

#### Krateo Template deep dive into technical definition

An example of a Krateo Template can be [*krateo-template-fireworksapp*](https://github.com/krateoplatformops/krateo-template-fireworksapp/blob/main/template.yaml), which aims to ask to the user the name of the application to release, the number of pods, the host to use to expose the application and the organization name for the git repository creation.

A Krateo Template doesn't have fixed specifications but it is represented by an array. Each element of the array is a *Widget*.

More details in a related issue.

### Krateo Deployment

A higher level *Composite Resource* that represents a group of *Managed Resources*.

Managed resources are granular, high fidelity Kubernetes representations of a resource in an external system.

Managed resources are what Krateo enables platform teams to compose into higher level composite resources, forming an opinionated platform API. They’re the building blocks of a Krateo Deployment.

Within a Krateo Deployment it is possible to specify which plugins are available in the Krateo UI Deployment section for a specific deployment instance.

#### Krateo Deployment deep dive into technical definition

An example of a Krateo Deployment can be [*kind: FireworksApp, apiVersion: deployment.krateo.io/v1alpha1*](https://github.com/krateoplatformops/krateo-template-fireworksapp/blob/main/deployment.yaml) where the managed resources are git repository, GitHub repository and an ArgoCD Application.

More details in a related issue.
