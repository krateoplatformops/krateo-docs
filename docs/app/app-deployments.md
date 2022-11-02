# Deployments

![deployments](../media/app/deployments.png)

Here you have the list of deployments created with Krateo.

## Deployment card

Every deployment card has the following information:

- icon
- title
- description
- tags
- creation date

If you want to see the details of a deployment, click on the card.

## Deployment details

Every deployment page has the following tabs in this order:

- overview
- _custom tabs_
- events
- values
- settings

### Overview

This tab shows the following information:

- description
- links

### Events

This tab shows the events of the deployment.
Every logs has

- source
- reason
- timestamp
- level (info, warning, error, debug)
- message

### Values

This tab shows the deployment.yaml file.

### Settings

From this tab you can delete the deployment.
This action is irreversible, but Krateo asks to you a confirm before delete deployment.

### Custom tabs

You can customize the deployment page with custom plugins.

Currently, Krateo has the following plugins:

- [argocd](#argocd)
- [kubernetes](#kubernetes)
- [doc](#doc)
- [pipeline](#pipeline)
- [capi](#capi-cluster-api)
- [keptn](#keptn)

#### Argocd

This plugin shows the ArgoCD application details, required values are

- `endpointName`: the name of the endpoint
- `icon`: fontawesome icon
- `name`: name of the tab
- `type`: argocd
- `value`: argocd application name

#### Kubernetes

This plugin shows the kubernetes components, selected by label, required values are

- `icon`: fontawesome icon
- `name`: name of the tab
- `type`: kubernetes
- `value`: label selector, eg. `app.kubernetes.io/name=nginx`. you can also use the deploymentId (value: deploymentId)

#### Doc

This plugin shows the markdown file from the repository, required values are

- `endpointName`: the name of the endpoint
- `icon`: fontawesome icon
- `name`: name of the tab
- `type`: doc
- `values`: list of files to render

  The form must be like this:
  `[organization_name][repository_name]file_name`

  For example:
  `'[krateoplatformops][guest-fire-smoked21]README.md'`
  (please note the single quotes around the value).

This plugins supports:

- GitHub
- Bitbucket (on-premise)

#### Pipeline

This plugin shows the list of last ten pipeline execution, required values are

- `endpointName`: the name of the endpoint
- `icon`: fontawesome icon
- `name`: name of the tab
- `type`: doc
- `values`: list of pipelines to fetch

  The form must be like this:
  `[organization_name][repository_name]file_name`

  For example:
  `'[krateoplatformops][guest-fire-smoked21]Build Docker image for every commit'`
  (please note the single quotes around the value).

This plugins supports:

- GitHub actions
- Jenkins

#### Capi (cluster api)

This plugin shows the cluster api config file, required values are

- `endpointName`: the name of the endpoint
- `icon`: fontawesome icon
- `name`: name of the tab
- `type`: capi
- `value`: cluster id

#### Keptn

This plugin shows the keptn delivery status, required values are

- `endpointName`: the name of the endpoint
- `icon`: fontawesome icon
- `name`: name of the tab
- `type`: keptn
- `value`: keptn project name + keptn service name

  eg. `'[krateo]demo'` (please note the single quotes around the value).

## Deployment.yaml

### Example

```yaml
# {{=<% %>=}}
---
apiVersion: deployment.krateo.io/v1alpha1
kind: FireworksApp
metadata:
  name: <%#norm%>{{name}}<%/norm%>-fireworksapp
spec:
  owner: mauro
  title: <% name %>
  description: Fireworks App Deployment
  icon: 'fa-solid fa-fire'
  tags:
    - fireworks
    - template
    - krateo
    - katy perry
  links:
    - url: https://github.com/<% organizationName %>/<% repositoryName %>
      title: <% organizationName %>/<% repositoryName %>
      icon: 'fa-brands fa-git'
  plugins:
    - name: resources
      value: <%#norm%>{{name}}<%/norm%>-fireworksapp
      type: argocd
      icon: fa-solid fa-diagram-project
      endpointName: argocd
    - name: documentation
      values:
        - '[krateoplatformops][<% owner %>-fire-<%#norm%>{{name}}<%/norm%>]README.md'
      type: doc
      icon: fa-solid fa-book
      endpointName: github
    - name: kubernetes
      value: deploymentId
      type: kubernetes
      icon: fa-brands fa-docker
    - name: pipelines
      values:
        - '[krateoplatformops][<% owner %>-fire-<%#norm%>{{name}}<%/norm%>]Build Docker image for every commit'
      type: pipeline
      icon: fa-solid fa-person-running
      endpointName: github
  values:
    replicas: <% replicas %>
    organizationName: krateoplatformops
    repositoryName: <% owner %>-fire-<%#norm%>{{name}}<%/norm%>
    destinationApiUrl: <% destinationEndpoint.target %>
    host: <% host %>
    description: Cause baby, you're a firework. Come on, show 'em what you're worth
    endpointName: <% destinationEndpoint.friendlyName %>
    namespace: krateo-system
    fromRepo:
      schema: https
      organizationName: krateoplatformops
      repositoryName: krateo-template-fireworksapp
    toRepo:
      schema: https
      organizationName: krateoplatformops
      repositoryName: <% owner %>-fire-<%#norm%>{{name}}<%/norm%>
      apiUrl: https://api.github.com
```

### Structure

- `apiVersion`: deployment.krateo.io/v1alpha1
- `kind`: _depends by the composition_

### Metadata

- `name`: name of the deployment

### Spec

- `owner`: owner of the template
- `title`: title of the template
- `description`: description of the template
- `icon`: fontawesome icon name. List of available icons is here [fontawesome.com](https://fontawesome.com/icons)
- `tags`: array of tags to identify your template
- `links`: array of links (overview tab)
- [plugins](#custom-tabs): list of plugins (tabs)
- `values`: list of values to render the template

#### Values

This is a object that contains the values to render the template.

You can specify properties with default value or getting the value from the form.

Here an example:

```yaml
values:
  organizationName: krateoplatformops
  repositoryName: <% repositoryName %>
```

`organizationName` has a default value, `repositoryName` is a value from the form.

## Endpoints

When you use a field as `endpoint` you can use the value like an object.
Endpoint object has this structure (for example):

```json
{
  "friendlyName": "krateo",
  "target": "https://krateo.io",
  "token": "token"
}
```

Use the target value like this:

```json
endpoint.target
```

## Functions

The deployment service supports some functions to manipulate the values.
Available functions are:

- `lower`: convert the value to lowercase
- `upper`: convert the value to uppercase
- `nospaces`: remove all spaces from the value
- `spacedash`: replace all spaces with dash
- `norm`: normalize the value (convert all spaces to dash and convert to lowercase)

The value inside the function must be enclosed by `{{` and `}}`.

### Example

```yaml
<%#norm%>{{name}}<%/norm%>
```
