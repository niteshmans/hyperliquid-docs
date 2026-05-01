# spotAssetCtxs

**POST** `wss://api.hyperliquid.xyz/wsMainnet`

`wss://api.hyperliquid.xyz/ws`\
`wss://api.hyperliquid-testnet.xyz/ws`

Subscription to context events for all spot assets.

## Body

`application/json`

Subscription to context events for all spot assets.

| Field  | Type               | Required | Description                                            |
| ------ | ------------------ | -------- | ------------------------------------------------------ |
| `type` | `undefined · enum` | Required | Type of subscription. Possible values: `spotAssetCtxs` |

## Responses

### 200

Event of spot asset contexts.

`application/json`

`SpotAssetCtxSchema[]` Optional

Event of spot asset contexts.

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.spotAssetCtxs((data) => {
  console.log(data);
});
```

## Response

```json
[]
```
