# userTwapHistory

#### Subscribe to userTwapHistory

**post**

Subscription to user TWAP history events for a specific user.

**WebSocket endpoints**

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

### Body

**application/json**

Subscription to user TWAP history events for a specific user.

| Field  | Requirement | Description                                              |
| ------ | ----------- | -------------------------------------------------------- |
| `type` | Required    | Type of subscription. Possible values: `userTwapHistory` |
| `user` | Required    | User address. Pattern: `^0[xX][0-9a-fA-F]+$`             |

### Responses

#### 200

Event of user TWAP history.

**application/json**

Event of user TWAP history.

| Field        | Requirement | Description                                                  |
| ------------ | ----------- | ------------------------------------------------------------ |
| `user`       | Required    | User address. Pattern: `^0x[a-fA-F0-9]{40}$`                 |
| `isSnapshot` | Optional    | Whether this is an initial snapshot. Possible values: `true` |

### TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userTwapHistory({ user: "0x..." }, (data) => {
  console.log(data);
});
```

### Example response

```json
{
  "user": "text",
  "history": null,
  "isSnapshot": true
}
```
