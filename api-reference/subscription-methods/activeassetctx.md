# activeAssetCtx

`post`

wss://api.hyperliquid.xyz/ws\
wss://api.hyperliquid-testnet.xyz/ws

Subscription to context events for a specific perpetual asset.

## Body

`application/json`

Subscription to context events for a specific perpetual asset.

* `type` `undefined` · `enum` **Required**\
  Type of subscription.\
  Possible values: `activeAssetCtx`
* `coin` `string` **Required**\
  Asset symbol (e.g., BTC).

## Responses

### 200

Event of active perpetual asset context.

`application/json`

Event of active perpetual asset context.

* `coin` `string` **Required**\
  Asset symbol (e.g., BTC).

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.activeAssetCtx({ coin: "ETH" }, (data) => {
  console.log(data);
});
```

```json
{
  "coin": "text",
  "ctx": null
}
```
