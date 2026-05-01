# orderStatus

`POST /info`

Request order status.

## Body

`application/json`

| Field  | Type                              | Required | Description                                                 |
| ------ | --------------------------------- | -------- | ----------------------------------------------------------- |
| `type` | `undefined` · enum                | Required | Type of request. Possible values: `orderStatus`             |
| `user` | `string` · min: 42 · max: 42      | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`                |
| `oid`  | any of                            | Required | Order ID or Client Order ID.                                |
| `oid`  | `integer` · max: 9007199254740991 | Optional | Order ID or Client Order ID.                                |
| `oid`  | `string` · min: 34 · max: 34      | Optional | Order ID or Client Order ID. Pattern: `^0[xX][0-9a-fA-F]+$` |

## Responses

### `200`

Order status response.

* If the order is found, returns detailed order information and its current status.
* If the order is not found, returns a status of `"unknownOid"`.

`application/json`

```json
{
  "status": "order",
  "order": {
    "order": null,
    "status": null,
    "statusTimestamp": 1
  }
}
```

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.orderStatus({ user: "0x...", oid: 12345 });
```
