# candle

`post`

**WebSocket endpoints**

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

Subscription to candlestick events for a specific asset and time interval.

## Body

`application/json`

Subscription to candlestick events for a specific asset and time interval.

| Field      | Type               | Required | Description               | Possible values / pattern                                                             |
| ---------- | ------------------ | -------- | ------------------------- | ------------------------------------------------------------------------------------- |
| `type`     | `undefined · enum` | Yes      | Type of subscription.     | `candle`                                                                              |
| `coin`     | `string`           | Yes      | Asset symbol (e.g., BTC). |                                                                                       |
| `interval` | `string · enum`    | Yes      | Time interval.            | `1m`, `3m`, `5m`, `15m`, `30m`, `1h`, `2h`, `4h`, `8h`, `12h`, `1d`, `3d`, `1w`, `1M` |

## Responses

### `200`

Event of candlestick data point.

`application/json`

| Field | Type            | Required | Description                           | Possible values / pattern                                                             |
| ----- | --------------- | -------- | ------------------------------------- | ------------------------------------------------------------------------------------- |
| `t`   | `number`        | Yes      | Opening timestamp (ms since epoch).   |                                                                                       |
| `T`   | `number`        | Yes      | Closing timestamp (ms since epoch).   |                                                                                       |
| `s`   | `string`        | Yes      | Asset symbol.                         |                                                                                       |
| `i`   | `string · enum` | Yes      | Time interval.                        | `1m`, `3m`, `5m`, `15m`, `30m`, `1h`, `2h`, `4h`, `8h`, `12h`, `1d`, `3d`, `1w`, `1M` |
| `o`   | `string`        | Yes      | Opening price.                        | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `c`   | `string`        | Yes      | Closing price.                        | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `h`   | `string`        | Yes      | Highest price.                        | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `l`   | `string`        | Yes      | Lowest price.                         | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `v`   | `string`        | Yes      | Total volume traded in base currency. | `^[0-9]+(\.[0-9]+)?$`                                                                 |
| `n`   | `number`        | Yes      | Number of trades executed.            |                                                                                       |

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.candle({ coin: "ETH", interval: "1h" }, (data) => {
  console.log(data);
});
```

## Example response

```json
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
```
