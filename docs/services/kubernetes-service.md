# Kubernetes Service

This service scan kubernetes cluster using a label selector

## Routes

### GET `/:selector/:params?`

- `selector` is the label selector to use
- `params` is an additional list of resources to scan (array of strings)

The resources are taken from this 2 files:

- [resources.json](https://github.com/krateoplatformops/kubernetes-service/blob/main/resources.json)
- [crd.json](https://github.com/krateoplatformops/kubernetes-service/blob/main/crd.json)

#### Example

Here we are looking for all resource with the label `deploymentId=b367d339-d848-446f-aee4-963a6e3cc0c1`

```bash
/deploymentId=b367d339-d848-446f-aee4-963a6e3cc0c1
```

#### Response

```json
{
  "list": [
    {
      "kind": "Object",
      "icon": "crd",
      "items": [ {...} ]
    },
    {
      "kind": "ProviderConfig",
      "icon": "crd",
      "items": [ {...} ]
    },
    {
      "kind": "Repo",
      "icon": "crd",
      "items": [ {...}, {...} ]
    },
    {
      "kind": "configmap",
      "icon": "cm",
      "items": [ {...} ]
    }
  ],
  "count": 4
}
```
