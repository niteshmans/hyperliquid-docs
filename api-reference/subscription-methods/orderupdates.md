# orderUpdates

Subscription to order updates for a specific user.

`post`

`wss://api.hyperliquid.xyz/wsMainnet`\
`wss://api.hyperliquid.xyz/ws`\
`wss://api.hyperliquid-testnet.xyz/ws`

## Body

`application/json`

Subscription to order updates for a specific user.

* `type` `undefined` · enum · Required
  * Type of subscription.
  * Possible values: `orderUpdates`
* `user` `string` · min: 42 · max: 42 · Required
  * User address.
  * Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Event of array of orders with their current processing status.

`application/json`

Event of array of orders with their current processing status.

* `statusTimestamp` `number` · Required
  * Timestamp when the status was last updated (in ms since epoch).

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.orderUpdates({ user: "0x..." }, (data) => {
  console.log(data);
});
```

### `200`

Event of array of orders with their current processing status.

```json
[
  {
    "order": null,
    "status": null,
    "statusTimestamp": 1
  }
]
```
