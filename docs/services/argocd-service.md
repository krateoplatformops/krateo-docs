# ArgoCD Service

This service is used to get resource tree or resource details from ArgoCD.

If you need to use this service you need to create an ArgoCD endpoint.

## Routes

### GET `/:endpoint/:name`

- `endpoint`: the name of the endpoint
- `name`: is the app name in ArgoCD

#### Example

This path is using the `argocd` endpoint to get the `firefire-fireworksapp` app.

```bash
argocd/firefire-fireworksapp
```

#### Response

```json
{
  "edges": [],
  "nodes": []
}
```

- `edges`: the list of connections between nodes
- `nodes`: the list of nodes

### GET `/:endpoint/:name?<params>`

- `endpoint`: the name of the endpoint
- `name`: is the app name in ArgoCD
- `params`: the info about the resource you want to get details

#### Example

This path is using the `argocd` endpoint to get the `firefire-fireworksapp` app.

```bash
argocd/firefire-fireworksapp?name=guest-fire-firefire-service&resourceName=guest-fire-firefire-service&namespace=guest-fire-firefire-ns&version=v1&kind=Service
```

#### Response

```json
{
  "manifest": {}
}
```

- `manifest`: the yaml manifest of the resource
