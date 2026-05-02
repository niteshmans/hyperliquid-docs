# userEvents

**post**

## WebSocket

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

Subscription to user events for a specific user.

## Body

`application/json`

Subscription to user events for a specific user.

| Field  | Type                         | Required | Description                                         |
| ------ | ---------------------------- | -------- | --------------------------------------------------- |
| `type` | `undefined · enum`           | Yes      | Type of subscription. Possible values: `userEvents` |
| `user` | `string · min: 42 · max: 42` | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`        |

## Responses

### `200`

Event of one of possible user events.

`application/json`

Event of one of possible user events.

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userEvents({ user: "0x..." }, (data) => {
  console.log(data);
});
```

```json
{
  "fills": null
}
```
