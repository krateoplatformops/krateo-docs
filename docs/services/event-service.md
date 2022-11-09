# Git Service

This service is used to get files from a git repository.

We can manage this types of git repository:

- github (public and private)
- bitbucket (on-premise)

Independently of the git service, this service needs an endpoint to get the files.

## Routes

### GET `/:deploymentId`

- `deploymentId`: is the id of the deployment

#### Example

This path is getting info about the deployment with id `b367d339-d848-446f-aee4-963a6e3cc0c1`.

```bash
b367d339-d848-446f-aee4-963a6e3cc0c1
```

#### Response

```json
{
  "list": [
    {
      "message": "cannot get object: applications.argoproj.io \"firefire-fireworksapp\" is forbidden: User \"system:serviceaccount:crossplane-system:provider-kubernetes-a1a49ab74384\" cannot get resource \"applications\" in API group \"argoproj.io\" in the namespace \"krateo-system\"",
      "time": 1668005542,
      "level": "warning",
      "reason": "CannotObserveExternalResource",
      "source": "firefire-fireworksapp-argocd-app-object",
      "deploymentId": "b367d339-d848-446f-aee4-963a6e3cc0c1"
    }
  ],
  "count": 1
}
```

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.

### POST `/`

Usually is the `event router` to post data here, the payload (with some edits) will be routed to the notification service.

#### Example

This is a sample event:

```json
{
  "type": "Warning",
  "reason": "CannotCreateExternalResource",
  "deploymentId": "",
  "time": 1660835529,
  "message": "cannot create EKS node group: ResourceInUseException: Cluster: test-1 is not in a valid state",
  "source": "managed/nodegroup",
  "involvedObject": {
    "apiVersion": "eks.aws.crossplane.io/v1alpha1",
    "kind": "NodeGroup",
    "name": "test-1-ng",
    "uid": "6365c158-8ee1-4d36-a33a-ba3cc0958ee0"
  },
  "metadata": {
    "creationTimestamp": "2022-10-26T17:25:12+02:00",
    "name": "test-1-ng.170c791ccd13d0cd",
    "namespace": "default",
    "uid": "6aa0a50b-1b5b-46e0-b5ec-a1118286f0c4"
  }
}
```

#### Response

```json
{
  "message": "ok"
}
```
