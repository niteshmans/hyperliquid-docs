# allDexsClearinghouseState

post

wss://api.hyperliquid.xyz/wsMainnet\
wss://api.hyperliquid.xyz/ws\
wss://api.hyperliquid-testnet.xyz/ws

Subscription to clearinghouse state events for all DEXs for a specific user.

## Body

| Field | Type                       | Required | Description                                                        |
| ----- | -------------------------- | -------- | ------------------------------------------------------------------ |
| type  | undefined · enum           | Required | Type of subscription. Possible values: `allDexsClearinghouseState` |
| user  | string · min: 42 · max: 42 | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`                       |

## Responses

### 200

Event of clearinghouse states for all DEXs for a specific user.

| Field               | Type      | Required | Description                                            |
| ------------------- | --------- | -------- | ------------------------------------------------------ |
| user                | string    | Required | User address. Pattern: `^0x[a-fA-F0-9]{40}$`           |
| clearinghouseStates | any\[]\[] | Required | Array of tuples of dex names and clearinghouse states. |

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.allDexsClearinghouseState({ user: "0x..." }, (data) => {
  console.log(data);
});
```

### 200

```json
{
  "user": "text",
  "clearinghouseStates": [\
    []\
  ]
}
```
