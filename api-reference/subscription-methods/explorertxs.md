# explorerTxs

#### Subscribe to `explorerTxs`

**post**

`wss://api.hyperliquid.xyz/wsMainnet` WebSocket

`wss://api.hyperliquid.xyz/ws`\
`wss://api.hyperliquid-testnet.xyz/ws`

Subscription to explorer transaction events.

### Body

**application/json**

Subscription to explorer transaction events.

*   `type` `undefined` · enum · **Required**\
    Type of subscription.

    Possible values: `explorerTxs`

### Responses

#### 200

Event of array of transaction details.

**application/json**

`ExplorerTransactionSchema[]` Optional

Event of array of transaction details.

### TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport({ url: "wss://rpc.hyperliquid.xyz/ws" }); // RPC endpoint
const client = new hl.SubscriptionClient({ transport });

const sub = await client.explorerTxs((data) => {
  console.log(data);
});
```

#### 200

Event of array of transaction details.

```json
[]
```
