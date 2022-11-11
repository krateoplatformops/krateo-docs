# Template Service

This service is used to manage templates.

## Routes

### GET `/`

Returns a list of all templates.

#### Response

```json
{
   "list":[
      {
         "apiVersion":"deployment.krateo.io/v1alpha1",
         "kind":"FireworksApp",
         "metadata":{
            "labels":{
               "crossplane.io/composite":"firefire-fireworksapp"
            },
            "name":"firefire-fireworksapp",
            "uid":"b367d339-d848-446f-aee4-963a6e3cc0c1"
         },
         "spec":{
            "compositionRef":{
               "name":"fireworksapp.deployment.krateo.io"
            },
            "compositionUpdatePolicy":"Automatic",
            "description":"Fireworks App Deployment",
            "icon":"fa-solid fa-fire",
            "links":[
              {...}
            ],
            "owner":"mauro",
            "plugins":[
               {...}
            ],
            "resourceRefs":[
               {...}
            ],
            "tags":[
               "fireworks",
               "template",
               "krateo",
               "katy perry"
            ],
            "title":"firefire",
            "values": {...}
         }
      }
   ],
   "count":1
}
```

### GET `/name/:name`

Get a template by name.

### GET `/uid/:uid`

Get a template by uid.

### POST `/`

This route is used to create a new template or refresh an existing template.

#### Example

```json
{
  "url": "https://github.com/krateoplatformops/krateo-template-fireworksapp/blob/main/template.yaml",
  "endpointName": "github"
}
```

#### Response

```json
{
   "apiVersion":"krateo.io/v1alpha1",
   "kind":"Template",
   "metadata":{
      "name":"krateo-fireworks",
      "uid":"385e9004-1717-4065-989a-34fb122a6de1"
   },
   "spec":{
      "description":"Krateo Fireworks Template",
      "endpointName":"github",
      "icon":"fa-solid fa-fire",
      "owner":"unknown",
      "tags":[
         "fireworks",
         "template",
         "krateo",
         "katy perry"
      ],
      "title":"Krateo Fireworks",
      "url":"https://github.com/krateoplatformops/krateo-template-fireworksapp/blob/main/template.yaml",
      "widgets":[ {...} ]
   }
}
```

### DELETE `/name/:name`

Delete a template by name.

#### Example

```bash
/name/my-awesome-template
```

#### Response

```json
{ "message": "Template with name my-awesome-template deleted" }
```

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.
