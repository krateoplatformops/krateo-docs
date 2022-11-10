# Provider Service

This service allows you to add/delete o list providers.

## Routes

### GET `/`

Returns a list of providers.

#### Response

```json
{
  "list": [
    {
      "kind": "Provider",
      "icon": "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDI1LjQuMCwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCAzNy45IDM4IiBzdHlsZT0iZW5hYmxlLWJhY2tncm91bmQ6bmV3IDAgMCAzNy45IDM4OyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+CjxzdHlsZSB0eXBlPSJ0ZXh0L2NzcyI+Cgkuc3Qwe2ZpbGw6IzAzQTlGNDt9Cgkuc3Qxe2ZpbGw6IzgxRDRGQTt9Cjwvc3R5bGU+CjxwYXRoIGNsYXNzPSJzdDAiIGQ9Ik0yOS40LDM4SDguNkMzLjksMzgsMCwzNC4xLDAsMjkuNFY4LjZDMCwzLjksMy45LDAsOC42LDBoMjAuN2M0LjgsMCw4LjYsMy45LDguNiw4LjZ2MjAuNwoJQzM4LDM0LjEsMzQuMSwzOCwyOS40LDM4eiIvPgo8cGF0aCBjbGFzcz0ic3QxIiBkPSJNMzEsMjkuNmMyLjUtMi44LDQtNi41LDQtMTAuNnMtMS41LTcuNy00LTEwLjZsMi44LTIuOGwwLDBsMi40LTIuNGMtMC40LTAuNS0wLjktMS0xLjQtMS40TDI5LjYsNwoJQzI2LjcsNC41LDIzLjEsMywxOSwzUzExLjMsNC41LDguNCw3TDMuMywxLjljLTAuNSwwLjQtMSwwLjktMS40LDEuNEw3LDguNEM0LjUsMTEuMywzLDE0LjksMywxOXMxLjUsNy43LDQsMTAuNmwtNS4xLDUuMQoJYzAuNCwwLjUsMC45LDEsMS40LDEuNGwyLjQtMi40bDAsMGwyLjgtMi44YzIuOCwyLjUsNi41LDQsMTAuNiw0czcuNy0xLjUsMTAuNi00bDUuMSw1LjFjMC41LTAuNCwxLTAuOSwxLjQtMS40TDMxLDI5LjZ6IE0zMywxOQoJYzAsMy41LTEuMyw2LjctMy40LDkuMkwyNiwyNC42YzEuMi0xLjUsMi0zLjUsMi01LjZzLTAuNy00LjEtMi01LjZsMy41LTMuNUMzMS43LDEyLjMsMzMsMTUuNSwzMywxOXogTTEyLDE5YzAtMS42LDAuNS0zLDEuNC00LjIKCWw0LjIsNC4ybC00LjIsNC4yQzEyLjUsMjIsMTIsMjAuNiwxMiwxOXogTTE5LDE3LjZsLTQuMi00LjJDMTYsMTIuNSwxNy40LDEyLDE5LDEyczMsMC41LDQuMiwxLjRMMTksMTcuNnogTTE5LDIwLjRsNC4yLDQuMgoJQzIyLDI1LjUsMjAuNiwyNiwxOSwyNnMtMy0wLjUtNC4yLTEuNEwxOSwyMC40eiBNMjAuNCwxOWw0LjItNC4yQzI1LjUsMTYsMjYsMTcuNCwyNiwxOXMtMC41LDMtMS40LDQuMkwyMC40LDE5eiBNMTksNQoJYzMuNSwwLDYuNywxLjMsOS4yLDMuNEwyNC42LDEyYy0xLjUtMS4yLTMuNS0yLTUuNi0ycy00LjEsMC43LTUuNiwyTDkuOSw4LjVDMTIuMyw2LjMsMTUuNSw1LDE5LDV6IE01LDE5YzAtMy41LDEuMy02LjcsMy40LTkuMgoJbDMuNSwzLjVjLTEuMiwxLjUtMiwzLjUtMiw1LjZzMC43LDQuMSwyLDUuNkw4LjQsMjhDNi4zLDI1LjcsNSwyMi41LDUsMTl6IE0xOSwzM2MtMy41LDAtNi43LTEuMy05LjItMy40bDMuNS0zLjUKCWMxLjUsMS4yLDMuNSwyLDUuNiwyczQuMS0wLjcsNS42LTJsMy41LDMuNUMyNS43LDMxLjcsMjIuNSwzMywxOSwzM3oiLz4KPC9zdmc+Cg==",
      "name": "provider-aws",
      "version": "v0.33.0",
      "healthy": "True"
    }
  ],
  "count": 1
}
```

### POST `/`

With this route you can apply json code to the cluster for to install a new provider.

The json is downloaded from the [catalog](https://github.com/krateoplatformops/catalog) repository and applied to the cluster.

#### Example

```json
{
  "apiVersion": "pkg.crossplane.io/v1",
  "kind": "Provider",
  "metadata": {
    "name": "provider-typeform"
  },
  "spec": {
    "package": "ghcr.io/krateoplatformops/provider-git:v1.2.5",
    "packagePullPolicy": "IfNotPresent"
  }
}
```

#### Response

```json
{ "message": "Created 1 resources of 1" }
```

### DELETE `/`

This router is used to delete a provider from the cluster.

#### Example

```json
{ "name": "provider-typeform", "kind": "Provider" }
```

#### Response

`status code 200`

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.
