# candleSnapshot

Request candlestick snapshots.

## Request body

`application/json`

| Field  | Type               | Required | Description         | Values / Pattern |
| ------ | ------------------ | -------: | ------------------- | ---------------- |
| `type` | `undefined · enum` |      Yes | Type of request.    | `candleSnapshot` |
| `req`  | `object`           |      Yes | Request parameters. |                  |

## Responses

### `200`

Array of candlestick data points.

`application/json`

| Field | Type            | Required | Description                           | Values / Pattern                                                                      |
| ----- | --------------- | -------: | ------------------------------------- | ------------------------------------------------------------------------------------- |
| `t`   | `number`        |      Yes | Opening timestamp (ms since epoch).   |                                                                                       |
| `T`   | `number`        |      Yes | Closing timestamp (ms since epoch).   |                                                                                       |
| `s`   | `string`        |      Yes | Asset symbol.                         |                                                                                       |
| `i`   | `string · enum` |      Yes | Time interval.                        | `1m`, `3m`, `5m`, `15m`, `30m`, `1h`, `2h`, `4h`, `8h`, `12h`, `1d`, `3d`, `1w`, `1M` |
| `o`   | `string`        |      Yes | Opening price.                        | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `c`   | `string`        |      Yes | Closing price.                        | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `h`   | `string`        |      Yes | Highest price.                        | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `l`   | `string`        |      Yes | Lowest price.                         | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `v`   | `string`        |      Yes | Total volume traded in base currency. | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `n`   | `number`        |      Yes | Number of trades executed.            |                                                                                       |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.candleSnapshot({
  coin: "ETH",
  interval: "1h",
  startTime: Date.now() - 1000 * 60 * 60 * 24,
});
```

## Test it

### `200`

Array of candlestick data points.

```json
[
  {
    "t": 1,
    "T": 1,
    "s": "text",
    "i": "1m",
    "o": "text",
    "c": "text",
    "h": "text",
    "l": "text",
    "v": "text",
    "n": 1
  }
]
```
