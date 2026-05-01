# l2Book

Request L2 order book.

Base URLs:

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

Request L2 order book.

| Field      | Type                       | Required | Description                                    | Possible values    |
| ---------- | -------------------------- | -------: | ---------------------------------------------- | ------------------ |
| `type`     | `undefined` · enum         | Required | Type of request.                               | `l2Book`           |
| `coin`     | `string`                   | Required | Asset symbol (e.g., BTC).                      |                    |
| `nSigFigs` | `any` of                   | Optional | Number of significant figures.                 |                    |
| `nSigFigs` | `number` · enum · nullable | Optional | Number of significant figures.                 | `2`, `3`, `4`, `5` |
| `mantissa` | `any` of                   | Optional | Mantissa for aggregation (if `nSigFigs` is 5). |                    |
| `mantissa` | `number` · enum · nullable | Optional | Mantissa for aggregation (if `nSigFigs` is 5). | `2`, `5`           |

## Responses

### `200`

L2 order book snapshot or `null` if the market does not exist.

`application/json`

\<object · nullable> Optional

Show properties

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

const data = await client.l2Book({ coin: "ETH", nSigFigs: 2 });
```

## Test it

### `200`

L2 order book snapshot or `null` if the market does not exist.

```json
{
  "coin": "text",
  "time": 1,
  "levels": [],
  "spread": "text"
}
```
