# jq

Given the json (Consul service):

```
[
  {
    "ID": "trololo-keyword",
    "Service": "trololo-service",
    "Tags": [
      "pouet",
      "alpha"
    ],
    "Meta": {
      "env": "prod",
      "path": "41261a55-b535-485e-9b5f-3ce11a507145",
      "sre_metrics": "101",
      "team": "keyword"
    },
    "Port": 443,
    "Address": "monitozebuloni",
    "Weights": {
      "Passing": 1,
      "Warning": 1
    },
    "EnableTagOverride": false
  }
  {
    "ID": "trololo2-keyword",
    "Service": "trololo2-service",
  ...
]
```

`curl http://api/v1/agent/services  | jq  '.[] | select( .ID | contains("keyword") )'`

  return services which have the `ID` value that contains the 'keyword' string


`curl http://api/v1/agent/services  | jq  '.[] | select( .Meta.sre_metrics ) )'`
  
  return services which have the `Meta['sre_metrics']` key defined


`curl http://api/v1/agent/services  | jq  '.[] | select(.Tags[]|contains("pouet"))'`
  
  return services which have the `"pouet"` Tags element defined

