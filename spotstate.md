# spotState

**POST** `wss://api.hyperliquid.xyz/ws`

`wss://api.hyperliquid-testnet.xyz/ws`

Subscription to spot state events for a specific user.

## Body

`application/json`

* `type` (undefined · enum, required): Type of subscription. Possible values: `spotState`
* `user` (string · min: 42 · max: 42, required): User address. Pattern: `^0[xX][0-9a-fA-F]+$`
* `ignorePortfolioMargin` (boolean, optional): Whether to ignore portfolio margin calculations.

## Responses

**200** — Event of user spot state.

`application/json`

* `user` (string, required): User address. Pattern: `^0x[a-fA-F0-9]{40}$`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.spotState({ user: "0x..." }, (data) => {
  console.log(data);
});
```

**200** — Event of user spot state.

```json
{
  "user": "text",
  "spotState": null
}
```
