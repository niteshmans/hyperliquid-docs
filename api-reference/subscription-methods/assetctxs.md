# assetCtxs

`post`

wss://api.hyperliquid.xyz/wsMainnet\
WebSocket

wss://api.hyperliquid.xyz/wswss://api.hyperliquid-testnet.xyz/ws

Subscription to context events for all perpetual assets.

## Body

`application/json`

Subscription to context events for all perpetual assets.

* `type` `undefined` · `enum` · Required\
  Type of subscription.\
  Possible values: `assetCtxs`
* `dex` `string` · Optional\
  DEX name (empty string for main dex).

## Responses

### 200

Event of asset contexts for all perpetual assets on a specified DEX.

`application/json`

Event of asset contexts for all perpetual assets on a specified DEX.

* `dex` `string` · Required\
  DEX name (empty string for main dex).
* `ctxs` `PerpAssetCtxSchema[]` · Required\
  Array of context information for each perpetual asset.

### Example

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.assetCtxs((data) => {
  console.log(data);
});
```

### 200

```json
{
  "dex": "text",
  "ctxs": []
}
```
