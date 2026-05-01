# openOrders

Subscription to open order events for a specific user.

## WebSocket endpoints

* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

## Body

| Field  | Type             | Required | Description                           | Constraints / values                                                  |
| ------ | ---------------- | -------- | ------------------------------------- | --------------------------------------------------------------------- |
| `type` | undefined · enum | Yes      | Type of subscription.                 | Possible values: `openOrders`                                         |
| `user` | string           | Yes      | User address.                         | <p>min: 42 · max: 42<br>Pattern: <code>^0[xX][0-9a-fA-F]+$</code></p> |
| `dex`  | string           | No       | DEX name (empty string for main dex). |                                                                       |

## Responses

### 200

Event of open orders for a specific user.

| Field  | Type   | Required | Description                           | Constraints / values           |
| ------ | ------ | -------- | ------------------------------------- | ------------------------------ |
| `dex`  | string | Yes      | DEX name (empty string for main dex). |                                |
| `user` | string | Yes      | User address.                         | Pattern: `^0x[a-fA-F0-9]{40}$` |

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.openOrders({ user: "0x..." }, (data) => {
  console.log(data);
});
```

### 200

Event of open orders for a specific user.

```json
{
  "dex": "text",
  "user": "text",
  "orders": null
}
```
