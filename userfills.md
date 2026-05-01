# userFills

Request array of user fills.

## Request body

`application/json`

| Field             | Type                         | Required | Description                                                                                |
| ----------------- | ---------------------------- | -------- | ------------------------------------------------------------------------------------------ |
| `type`            | `undefined · enum`           | Required | Type of request. Possible values: `userFills`                                              |
| `user`            | `string · min: 42 · max: 42` | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`                                               |
| `aggregateByTime` | `boolean`                    | Optional | If true, partial fills are aggregated when a crossing order fills multiple resting orders. |

## Responses

### `200`

Array of user trade fills.

`application/json`

#### Response fields

| Field           | Type                | Required | Description                                                                                   |
| --------------- | ------------------- | -------- | --------------------------------------------------------------------------------------------- |
| `cloid`         | `string`            | Optional | Client Order ID. Pattern: `^0x[a-fA-F0-9]{32}$`                                               |
| `liquidation`   | `object`            | Optional | Liquidation details.                                                                          |
| `coin`          | `string`            | Required | Asset symbol.                                                                                 |
| `px`            | `string`            | Required | Price. Pattern: `^[0-9]+(\\.[0-9]+)?$`                                                        |
| `sz`            | `string`            | Required | Size. Pattern: `^[0-9]+(\\.[0-9]+)?$`                                                         |
| `side`          | `string · enum`     | Required | Order side (`"B"` = Bid/Buy, `"A"` = Ask/Sell). Possible values: `B`, `A`                     |
| `time`          | `number`            | Required | Timestamp when the trade occurred (in ms since epoch).                                        |
| `startPosition` | `string`            | Required | Start position size. Pattern: `^-?[0-9]+(\\.[0-9]+)?$`                                        |
| `dir`           | `string`            | Required | Direction indicator for frontend display.                                                     |
| `closedPnl`     | `string`            | Required | Realized PnL. Pattern: `^-?[0-9]+(\\.[0-9]+)?$`                                               |
| `hash`          | `string`            | Required | L1 transaction hash. Pattern: `^0x[a-fA-F0-9]{64}$`                                           |
| `oid`           | `number`            | Required | Order ID.                                                                                     |
| `crossed`       | `boolean`           | Required | Indicates if the fill was a taker order.                                                      |
| `fee`           | `string`            | Required | Fee charged or rebate received (negative indicates rebate). Pattern: `^-?[0-9]+(\\.[0-9]+)?$` |
| `builderFee`    | `string`            | Optional | Optional fee charged by the UI builder. Pattern: `^-?[0-9]+(\\.[0-9]+)?$`                     |
| `tid`           | `number`            | Required | Unique transaction identifier for a partial fill of an order.                                 |
| `feeToken`      | `string`            | Required | Token in which the fee is denominated (e.g., `"USDC"`).                                       |
| `twapId`        | `number · nullable` | Required | ID of the TWAP.                                                                               |

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

### `500`

Internal Server Error.

`application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userFills({ user: "0x..." });
```

## Test it

### `200`

Array of user trade fills.

```json
[
  {
    "cloid": "text",
    "liquidation": {
      "liquidatedUser": "text",
      "markPx": "text",
      "method": "market"
    },
    "coin": "text",
    "px": "text",
    "sz": "text",
    "side": "B",
    "time": 1,
    "startPosition": "text",
    "dir": "text",
    "closedPnl": "text",
    "hash": "text",
    "oid": 1,
    "crossed": true,
    "fee": "text",
    "builderFee": "text",
    "tid": 1,
    "feeToken": "text",
    "twapId": 1
  }
]
```
