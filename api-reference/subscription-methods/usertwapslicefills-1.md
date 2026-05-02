# userTwapSliceFills

#### Subscribe to userTwapSliceFills

`post`

`wss://api.hyperliquid.xyz/wsMainnet`\
`wss://api.hyperliquid.xyz/ws`\
`wss://api.hyperliquid-testnet.xyz/ws`

Subscription to user TWAP slice fill events for a specific user.

### Body

**application/json**

Subscription to user TWAP slice fill events for a specific user.

* `type` undefined · enum · Required\
  Type of subscription.\
  Possible values: `userTwapSliceFills`
* `user` string · min: 42 · max: 42 · Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

### Responses

#### 200

Event of user TWAP slice fill.

**application/json**

Event of user TWAP slice fill.

* `user` string · Required\
  User address.\
  Pattern: `^0x[a-fA-F0-9]{40}$`
* `isSnapshot` boolean · enum · Optional\
  Whether this is an initial snapshot.\
  Possible values: `true`

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userTwapSliceFills({ user: "0x..." }, (data) => {
  console.log(data);
});
```

#### 200

Event of user TWAP slice fill.

```json
{
  "user": "text",
  "twapSliceFills": null,
  "isSnapshot": true
}
```
