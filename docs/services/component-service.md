# Component Service

This service returns the status of Krateo components.

It scans all the kubernetes services in the current namespace using this selectors:

```
app.kubernetes.io/component=service
app.kubernetes.io/part-of=krateo
```

## Routes

### GET `/`

Returns the status of all components.

#### Response

```json
{
  "list": [{ "name": "argocd-service", "status": 200, "statusText": "OK" }],
  "count": 1
}
```
