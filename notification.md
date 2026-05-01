# notification

#### Subscribe to notification

**post**

```
wss://api.hyperliquid.xyz/ws
wss://api.hyperliquid-testnet.xyz/ws
```

Subscription to notification events for a specific user.

### Body

**application/json**

Subscription to notification events for a specific user.

* `type` — **Required**\
  Type of subscription.\
  Possible values: `notification`
* `user` — **Required**\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

### Responses

#### 200

Event of user notification.

**application/json**

Event of user notification.

* `notification` — **Required**\
  Notification content.

### TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.notification({ user: "0x..." }, (data) => {
  console.log(data);
});
```

#### 200

```json
{
  "notification": "text"
}
```
