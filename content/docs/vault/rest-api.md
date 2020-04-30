---
title: "Rest Api"
date: 2020-04-18T20:44:03-07:00
draft: false
---

```sh
vault kv put secret/foo a=b
vault kv get secret/foo
```

## REST API

Notice `data` in the JSON and in the URL path.

```json
{
  "data": {
    "foo": "bar",
    "zip": "zap"
  }
}
```

```sh
curl -sS -X POST -H "X-Vault-Token: ${VAULT_TOKEN}"  --data @payload.json   http://127.0.0.1:8200/v1/secret/data/foo
curl -sS -X GET -H "X-Vault-Token: ${VAULT_TOKEN}"  http://127.0.0.1:8200/v1/secret/data/foo
```
