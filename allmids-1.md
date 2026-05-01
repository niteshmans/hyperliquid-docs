# allMids

**post**

**WebSocket endpoint**

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

Subscription to mid price events for all coins.

## Body

**application/json**

Subscription to mid price events for all coins.

* `type` `undefined` · enum · Required\
  Type of subscription.\
  Possible values: `allMids`
* `dex` `string` · Optional\
  DEX name (empty string for main dex).

## Responses

**200**

Event of mid prices for all assets.

**application/json**

Event of mid prices for all assets.

* `dex` `string` · Optional\
  DEX name (empty string for main dex).

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.allMids((data) => {
  console.log(data);
});
```

## Example response

```json
{
  "mids": null,
  "dex": "text"
}
```
