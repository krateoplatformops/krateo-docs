# Deployment Service

This service is used to manage deployments.

## Routes

### GET `/`

Get alle deployments.

#### Response

```json
{
   "list":[
      {
         "apiVersion":"deployment.krateo.io/v1alpha1",
         "kind":"FireworksApp",
         "metadata": {...},
         "spec": {...}
      }
   ],
   "count":1
}
```

### GET `/:uid`

This controller returns a deployment by uid, but it scans all the deployments independently by kind, so this is slower than the subsequent route.

#### Example

```bash
b367d339-d848-446f-aee4-963a6e3cc0c1
```

#### Response

```json
{
    "apiVersion":"deployment.krateo.io/v1alpha1",
    "kind":"FireworksApp",
    "metadata": {...},
    "spec": {...}
}
```

### GET `/:kind/:uid`

Get a deployment by kind and uid (faster than previous route).

#### Example

```bash
FireworksApp/b367d339-d848-446f-aee4-963a6e3cc0c1
```

#### Response

```json
{
    "apiVersion":"deployment.krateo.io/v1alpha1",
    "kind":"FireworksApp",
    "metadata": {...},
    "spec": {...}
}
```

### POST `/`

Create a deployment from a template form.

#### Example

```json
{
  "metadata": {
    "name": "firefire",
    "replicas": "1",
    "host": "fireworks.krateo.site",
    "organizationName": "krateoplatformops",
    "destinationEndpoint": "argocd",
    "owner": "guest"
  },
  "templateId": "385e9004-1717-4065-989a-34fb122a6de1"
}
```

#### Response

```json
{
    "apiVersion":"deployment.krateo.io/v1alpha1",
    "kind":"FireworksApp",
    "metadata": {...},
    "spec": {...}
}
```

### DELETE `/`

Delete a deployment.

#### Example

```json
{
  "apiVersion": "deployment.krateo.io/v1alpha1",
  "kind": "FireworksApp",
  "name": "aaaa-fireworksapp",
  "uid": "cc742bb0-19ca-469b-8c2d-187b0aaf019e"
}
```

#### Response

```json
{ "message": "Deployment with name aaaa-fireworksapp deleted" }
```
