# trades

**post**

`wss://api.hyperliquid.xyz/wsMainnet` WebSocket

`wss://api.hyperliquid.xyz/ws` `wss://api.hyperliquid-testnet.xyz/ws`

Subscription to trade events for a specific asset.

## Body

`application/json`

Subscription to trade events for a specific asset.

* `type` **undefined · enum** — Required\
  Type of subscription.\
  Possible values: `trades`
* `coin` **string** — Required\
  Asset symbol (e.g., BTC).

## Responses

**200**

Event of array of trades for a specific asset.

`application/json`

any Optional

Event of array of trades for a specific asset.

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.trades({ coin: "ETH" }, (data) => {
  console.log(data);
});
```

**200**

Event of array of trades for a specific asset.

```
No content
```
