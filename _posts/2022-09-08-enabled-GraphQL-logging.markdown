---
layout: post
title:  "How to enable GraphQL logging"
date:   2022-09-08 12:58
categories: GraphQL Logging
---
# How to enable GraphQL logging

Edit the host.json file within the GraphQL server folder

Make sure there is a `Function.graphql` setting that is Information (or whatever loglevel you need)

**!! IMPORTANT !!:** *Do not commit/push this or it will result in lots of logging going into application insights*

```json
{
  "version": "2.0",
  "extensionBundle": {
    "id": "Microsoft.Azure.Functions.ExtensionBundle",
    "version": "[1.*, 3.0.0)"
  },
  "logging": {
    "fileLoggingMode": "always",
    "logLevel": {
      "default": "Error",
      "Function.graphql": "Information"
    }
  },
  "extensions": {
    "http": {
        "routePrefix": ""
    }
  }
}
```
