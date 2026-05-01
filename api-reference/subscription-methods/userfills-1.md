# userFills

`post`

`wss://api.hyperliquid.xyz/wsMainnet` WebSocket

`wss://api.hyperliquid.xyz/ws`\
`wss://api.hyperliquid-testnet.xyz/ws`

Subscription to user fill events for a specific user.

## Body

`application/json`

Subscription to user fill events for a specific user.

*   `type` undefined · enum · Required\
    Type of subscription.

    Possible values: `userFills`
*   `user` string · min: 42 · max: 42 · Required\
    User address.

    Pattern: `^0[xX][0-9a-fA-F]+$`
* `aggregateByTime` boolean · Optional\
  If true, partial fills are aggregated when a crossing order fills multiple resting orders.

## Responses

### `200`

Event of user trade fill.

`application/json`

Event of user trade fill.

*   `user` string · Required\
    User address.

    Pattern: `^0x[a-fA-F0-9]{40}$`
*   `isSnapshot` boolean · enum · Optional\
    Whether this is an initial snapshot.

    Possible values: `true`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userFills({ user: "0x..." }, (data) => {
  console.log(data);
});
```

### `200`

Event of user trade fill.

```json
{
  "user": "text",
  "fills": null,
  "isSnapshot": true
}
```
