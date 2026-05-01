# allDexsAssetCtxs

`post`

`wss://api.hyperliquid.xyz/wsMainnet`

`wss://api.hyperliquid.xyz/wswss://api.hyperliquid-testnet.xyz/ws`

Subscription to asset context events for all DEXs.

## Body

`application/json`

Subscription to asset context events for all DEXs.

*   `type` `undefined` · enum · Required\
    Type of subscription.

    Possible values: `allDexsAssetCtxs`

## Responses

### `200`

Event of asset contexts for all DEXs.

`application/json`

Event of asset contexts for all DEXs.

* `ctxs` `any[][]` · Required\
  Array of tuples of dex names and contexts for each perpetual asset.

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.allDexsAssetCtxs((data) => {
  console.log(data);
});
```

## Example response

```json
{
  "ctxs": [\
    []\
  ]
}
```
