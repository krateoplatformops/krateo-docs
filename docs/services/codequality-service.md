# Code Quality Service

This service is used to check the code quality of a project.

Currently we support this service:

- sonarcloud/sonarqube

## Routes

### GET `/:endpointName/:key`

- `endpointName` - The name of the endpoint to use.
- `key` - The key of the project to check. This is the project key in sonarcloud/sonarqube.

#### Example

```bash
/sonarcloud/maurosala_fat-squirrels
```

#### Response

```json
{
  "component": {
    "organization": "maurosala",
    "key": "maurosala_fat-squirrels",
    "name": "fat-squirrels",
    "qualifier": "TRK",
    "analysisDate": "2022-04-15T16:23:33+0200",
    "tags": [],
    "visibility": "public",
    "leakPeriodDate": "2021-10-28T11:52:16+0200",
    "version": "not provided"
  },
  "metrics": [
    {
      "metric": "alert_status",
      "label": "alert status",
      "value": "OK",
      "color": "Green",
      "icon": "fa-solid fa-exclamation-triangle",
      "category": "alerts"
    },
    { ... }
  ],
  "link": "https://sonarcloud.io/project/overview?id=maurosala_fat-squirrels"
}
```
