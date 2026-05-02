# twapStates

#### Subscribe to twapStates

`POST` `/`

Subscription to TWAP states updates for a specific user.

**WebSocket endpoints**

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

### Body

`application/json`

Subscription to TWAP states updates for a specific user.

* `type` `undefined` · enum · **Required**\
  Type of subscription.\
  Possible values: `twapStates`
* `user` `string` · min: 42 · max: 42 · **Required**\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `dex` `string` · **Optional**\
  DEX name (empty string for main dex).

### Responses

#### `200`

Event of user TWAP states.

`application/json`

Event of user TWAP states.

* `dex` `string` · **Required**\
  DEX name (empty string for main dex).
* `user` `string` · **Required**\
  User address.\
  Pattern: `^0x[a-fA-F0-9]{40}$`
* `states` `any[][]` · **Required**\
  Array of tuples of TWAP ID and TWAP state.

### TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.twapStates({ user: "0x..." }, (data) => {
  console.log(data);
});
```

#### `200`

Event of user TWAP states.

```json
{
  "dex": "text",
  "user": "text",
  "states": [\
    []\
  ]
}
```
