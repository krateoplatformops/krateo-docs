# Secret Service

## GET `/:group`

This route returns a list of secrets in the group.

The available groups are:

- secret
- endpoint

### Example

```bash
/endpoint
```

### Response

```json
{
  "list": [
    {
      "metadata": {
        "name": "argocd-endpoint",
        "namespace": "krateo-system",
        "group": "endpoint",
        "uid": "51b5b4ec-d198-42af-b2a8-ac999579cc96",
        "icon": "fa-solid fa-charging-station",
        "type": "argocd",
        "category": "delivery"
      },
      "friendlyName": "argocd",
      "target": "http://argo-argocd-server.krateo-system.svc"
    }
  ],
  "count": 1
}
```

## GET `/:group/:name`

This route is the same of the above, but return only one secret/endpoint and it return all the data (sensitive data).

### Example

```bash
/secret/sample
```

### Response

```json
{
  "metadata": {
    "name": "sample-secret",
    "namespace": "krateo-system",
    "group": "secret",
    "uid": "3f60dad4-8963-49df-8bab-5edb672de67f",
    "icon": "fa-solid fa-toilet-paper",
    "type": "custom"
  },
  "friendlyName": "sample",
  "data": { "sample_key": "sample_value" }
}
```

## POST `/:group`

This route is used to create a new secret/endpoint.

### Example

```bash
/secret
```

```json
{
  "icon": "fa-solid fa-toilet-paper",
  "name": "sample",
  "type": "custom",
  "secret": { "sample_key": "sample_val" }
}
```

### Response

```json
{
  "metadata": {
    "name": "sample-secret",
    "namespace": "krateo-system",
    "group": "secret",
    "uid": "e18442a5-1986-486d-92a8-5104da846822",
    "icon": "fa-solid fa-toilet-paper",
    "type": "custom"
  },
  "friendlyName": "sample"
}
```

## DELETE `/:group/:name`

This route is used to delete a secret/endpoint.

### Example

```bash
/secret/sample
```

### Response

```json
{ "message": "Secret sample deleted" }
```

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.
