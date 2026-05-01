# clearinghouseState

`post` `/`

Subscription to clearinghouse state events for a specific user.

## WebSocket endpoints

* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

## Body

`application/json`

| Field  | Type                         | Required | Description                                                 |
| ------ | ---------------------------- | -------- | ----------------------------------------------------------- |
| `type` | `undefined` · enum           | Required | Type of subscription. Possible values: `clearinghouseState` |
| `user` | `string` · min: 42 · max: 42 | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`                |
| `dex`  | `string`                     | Optional | DEX name (empty string for main dex).                       |

## Responses

### `200`

Event of clearinghouse state for a specific user.

`application/json`

| Field  | Type     | Required | Description                                  |
| ------ | -------- | -------- | -------------------------------------------- |
| `dex`  | `string` | Required | DEX name (empty string for main dex).        |
| `user` | `string` | Required | User address. Pattern: `^0x[a-fA-F0-9]{40}$` |

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.clearinghouseState({ user: "0x..." }, (data) => {
  console.log(data);
});
```

## Example response

```json
{
  "dex": "text",
  "user": "text",
  "clearinghouseState": null
}
```
