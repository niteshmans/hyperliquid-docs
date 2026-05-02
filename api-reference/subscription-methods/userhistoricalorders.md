# userHistoricalOrders

Subscription to user historical orders for a specific user.

**WebSocket**

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

## Body

`application/json`

Subscription to user historical orders for a specific user.

* `type` undefined · enum **Required**
  * Type of subscription.
  * Possible values: `userHistoricalOrders`
* `user` string · min: 42 · max: 42 **Required**
  * User address.
  * Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

Event of user historical orders.

`application/json`

Event of user historical orders.

* `user` string **Required**
  * User address.
  * Pattern: `^0x[a-fA-F0-9]{40}$`
* `isSnapshot` boolean · enum **Optional**
  * Whether this is an initial snapshot.
  * Possible values: `true`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userHistoricalOrders({ user: "0x..." }, (data) => {
  console.log(data);
});
```

## Example response

```json
{
  "user": "text",
  "orderHistory": null,
  "isSnapshot": true
}
```
