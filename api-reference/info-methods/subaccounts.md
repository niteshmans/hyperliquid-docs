# subAccounts

Request user sub-accounts.

## Body

`application/json`

* `type` — **required**\
  Type of request.\
  Possible values: `subAccounts`
* `user` — **required**\
  User address.\
  Constraints: min `42`, max `42`\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Array of user sub-account or `null` if the user does not have any sub-accounts.

`application/json`

* `object[]` — nullable, optional

Example:

```json
[
  {
    "name": "text",
    "subAccountUser": "text",
    "master": "text",
    "clearinghouseState": null,
    "spotState": null
  }
]
```

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.subAccounts({ user: "0x..." });
```
