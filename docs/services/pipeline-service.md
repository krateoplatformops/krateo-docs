# Pipeline Service

This service is used to retrieve information about pipelines.

Currently, we support this tipe of pipelines:

- GitHub
- Jenkins

## Routes

### GET `/:endpointName/:pipelines`

- `endpointName` is the name of the endpoint to use
- `pipelines` is the list of pipelines to retrieve, separated by a comma if multiple pipelines

#### Example

```bash
github/%5Bkrateoplatformops%5D%5Bguest-fire-firefire%5DBuild%20Docker%20image%20for%20every%20commit
```

as you can see the pipeline list is encoded in the path.

#### Response

```json
{
  "list": [
    {
      "pipeline": {
        "id": 40226801,
        "name": "Build Docker image for every commit",
        "icon": "fa-brands fa-github",
        "link": "https://github.com/krateoplatformops/guest-fire-firefire/blob/main/.github/workflows/docker-build.yaml"
      },
      "runs": [
        {
          "id": 3443489775,
          "branch": "main",
          "url": "https://github.com/krateoplatformops/guest-fire-firefire/actions/runs/3443489775",
          "status": "failure",
          "time": 1668154209,
          "message": ":rocket: first commit",
          "duration": 28
        }
      ]
    }
  ],
  "count": 1
}
```

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.
