# Notification Service

This service is used to receive and send notifications to the App.

### WS `/`

This endpoint is used to connect by web socket to the Krateo App.

### POST `/`

This endpoint receives a JSON to push by socket.io to the Krateo App.

#### Example

This is a sample payload:

```json
{
  "message": "Hello World",
  "time": 1652260914,
  "level": "debug",
  "reason": "test",
  "source": "insomnia",
  "deploymentId": "62ab322906b13e186722a1ad"
}
```

#### Response

```json
{
  "message": "ok"
}
```
