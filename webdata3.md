# webData3

**post**

`wss://api.hyperliquid.xyz/ws`

`wss://api.hyperliquid-testnet.xyz/ws`

Subscription to comprehensive user and market data events.

## Body

`application/json`

Subscription to comprehensive user and market data events.

* `type` — **required**. Type of subscription. Possible values: `webData3`
* `user` — **required**. User address. Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

Event of comprehensive user and market data.

`application/json`

Event of comprehensive user and market data.

* `userState` object — **required**
* `perpDexStates` object\[] — **required**

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.webData3({ user: "0x..." }, (data) => {
  console.log(data);
});
```

## 200 response example

```json
{
  "userState": {
    "agentAddress": "text",
    "agentValidUntil": 1,
    "cumLedger": "text",
    "serverTime": 1,
    "isVault": true,
    "user": "text",
    "optOutOfSpotDusting": true,
    "dexAbstractionEnabled": true,
    "abstraction": "dexAbstraction"
  },
  "perpDexStates": [
    {
      "totalVaultEquity": "text",
      "perpsAtOpenInterestCap": null,
      "leadingVaults": null
    }
  ]
}
```
