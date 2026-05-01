# activeAssetData

#### Subscribe to activeAssetData

`post`

wss://api.hyperliquid.xyz/ws\
wss://api.hyperliquid-testnet.xyz/ws

Subscription to active asset data events for a specific user and coin.

### Body

`application/json`

Subscription to active asset data events for a specific user and coin.

* `type` `undefined` · `enum` **Required**\
  Type of subscription.\
  Possible values: `activeAssetData`
* `coin` `string` **Required**\
  Asset symbol (e.g., BTC).
* `user` `string` · min: 42 · max: 42 **Required**\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

### Responses

#### 200

Event of user active asset data.

`application/json`

`any` Optional

Event of user active asset data.

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.activeAssetData({ coin: "ETH", user: "0x..." }, (data) => {
  console.log(data);
});
```

#### 200

Event of user active asset data.

```
No content
```
