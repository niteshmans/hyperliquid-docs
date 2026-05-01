# userDetails

Request array of user transaction details.

## Body

`application/json`

* `type` — string · enum · required\
  Type of request.\
  Possible values: `userDetails`
* `user` — string · min: 42 · max: 42 · required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Response array of user transaction details.

`application/json`

* `type` — string · enum · required\
  Type of response.\
  Possible values: `userDetails`
* `txs` — `ExplorerTransactionSchema[]` · required\
  Array of user transaction details.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userDetails({ user: "0x..." });
```

## Test it

### `200`

Response array of user transaction details.

```json
{
  "type": "userDetails",
  "txs": []
}
```
