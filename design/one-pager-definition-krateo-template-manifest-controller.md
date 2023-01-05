# Definition of Krateo Template manifest and controller

* Owner: Diego Braga (@braghettos)
* Reviewers: Krateo Maintainers
* Status: Draft, revision 1.0

## Background

A Krateo Template should be handled by a Kubernetes controller to guarantee consistency between the Template and the related Krateo Module definiton.

## Goals

Scope of this definition is to put all the logic for handling a Krateo Template in a Kubernetes controller and offload the UI from this purpose.

## Proposal

1. Key values within a Krateo Template (like https://github.com/krateoplatformops/krateo-template-fireworksapp/blob/main/template.yaml#L48) must be aligned with the spec property of the related Krateo Module (like https://github.com/krateoplatformops/krateo-template-fireworksapp/blob/main/fireworskapp/definition.yaml#L70). If there is a key value in the Krateo Template instance that is not present in the Krateo Module definition, then the Krateo Template manifest cannot not be applied. An error will be shown providing the evidence on the single or multiple mismatch.
2. Since key values must be aligned with Krateo Module definition, they can be nested as well (i.e. `fromRepo.schema`).
3. A Krateo Template manifest cannot be applied if the related Krateo Module is not previously installed. The Krateo Template controller will understand which Krateo Module the Krateo Template is related thanks to a proper section within Krateo Template specs - ideally as a [dependency](https://doc.crds.dev/github.com/crossplane/crossplane/meta.pkg.crossplane.io/Configuration/v1@v1.10.1#spec-dependsOn).
5. A Krateo Template manifest must provide the ability to specify regex for each input field.
6. The deletion of a Krateo Template removes the related Krateo Module. If the Platform Teams wants to still let a user request a Krateo Deployment via Kubernetes manifest, then the Krateo Module can be installed with the related manifest.
7. A Krateo Template can be used also to edit a Krateo Deployment. There is the option for the Platform Team to let the user edit just some fields, so the Krateo Template manifest will provide the option to specify if a field is editable or not.

## Krateo Template manifest

## Krateo Template controller
