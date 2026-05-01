# webData2

**post**

**WebSocket endpoints**

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

Subscription to comprehensive user and market data events.

## Body

`application/json`

Subscription to comprehensive user and market data events.

* `type` — enum, required\
  Type of subscription.\
  Possible values: `webData2`
* `user` — string, required\
  User address.\
  Min: 42 · Max: 42\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

Event of comprehensive user and market data.

`application/json`

`any` — Optional

Event of comprehensive user and market data.

## Example

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.webData2({ user: "0x..." }, (data) => {
  console.log(data);
});
```

### 200

Event of comprehensive user and market data.

```
No content
```
