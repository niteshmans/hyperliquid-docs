# subAccounts2

`POST /info`

## Body

`application/json`

| Field  | Type                         | Required | Description                                      |
| ------ | ---------------------------- | -------- | ------------------------------------------------ |
| `type` | `undefined` · enum           | Required | Type of request. Possible values: `subAccounts2` |
| `user` | `string` · min: 42 · max: 42 | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`     |

## Responses

### 200

Array of user sub-account or null if the user does not have any sub-accounts.

`application/json`

`object[]` · nullable · Optional

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.subAccounts2({ user: "0x..." });
```

## Example response

`200`

Array of user sub-account or null if the user does not have any sub-accounts.

```json
[
  {
    "name": "text",
    "subAccountUser": "text",
    "master": "text",
    "dexToClearinghouseState": [
      []
    ],
    "spotState": null
  }
]
```
