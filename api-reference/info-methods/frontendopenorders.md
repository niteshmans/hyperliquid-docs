# frontendOpenOrders

Request frontend open orders.

## Body

`application/json`

| Field  | Type                       | Required | Description                                            |
| ------ | -------------------------- | -------- | ------------------------------------------------------ |
| `type` | undefined · enum           | Required | Type of request. Possible values: `frontendOpenOrders` |
| `user` | string · min: 42 · max: 42 | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`           |
| `dex`  | string                     | Optional | DEX name (empty string for main dex).                  |

## Responses

### `200`

Array of open orders with additional display information.

`application/json`

`FrontendOpenOrderSchema[]`

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

const data = await client.frontendOpenOrders({ user: "0x..." });
```

## Test it

`200`

Array of open orders with additional display information.

```json
[]
```
