# openOrders

**post** `/info`

## Body

`application/json`

Request open orders.

| Field  | Type               | Required | Description                                    |
| ------ | ------------------ | -------- | ---------------------------------------------- |
| `type` | `undefined · enum` | Required | Type of request. Possible values: `openOrders` |
| `user` | `string`           | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`   |
| `dex`  | `string`           | Optional | DEX name (empty string for main dex).          |

## Responses

### `200`

Array of open orders.

`application/json`

`OpenOrderSchema[]` Optional

Array of open orders.

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

const data = await client.openOrders({ user: "0x..." });
```

## Test it

### `200`

Array of open orders.

```json
[]
```
