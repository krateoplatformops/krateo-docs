# Keptn Service

This is a template for a Keptn service. You can find more info about Keptn services in the [Keptn docs](https://keptn.sh/docs/).

## Routes

### GET `/project/:endpoint/:name`

This route is used to get the project with the given name.

- `endpointName`: the name of the endpoint
- `name`: it the name of the project on Keptn

#### Example

```bash
/project/keptn/krateo-prj
```

### POST `/trigger/:endpoint/:name`

#### Example

```bash
/trigger/keptn/krateo-prj
```

```json
{
  "contenttype": "application/json",
  "type": "`sh.keptn.event.stage.sequence.triggered`",
  "source": "bridge",
  "data": {
    "project": "project",
    "stage": "stage",
    "service": "service"
  }
}
```

#### Response

```json
{ "message": "Event triggered" }
```

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.
