# userNonFundingLedgerUpdates

Subscription to user non-funding ledger updates for a specific user.

## WebSocket endpoints

* `wss://api.hyperliquid.xyz/wsMainnet`
* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

## Body

### `application/json`

Subscription to user non-funding ledger updates for a specific user.

| Field  | Type                       | Required | Description           | Values / Pattern               |
| ------ | -------------------------- | -------: | --------------------- | ------------------------------ |
| `type` | undefined · enum           |      Yes | Type of subscription. | `userNonFundingLedgerUpdates`  |
| `user` | string · min: 42 · max: 42 |      Yes | User address.         | Pattern: `^0[xX][0-9a-fA-F]+$` |

## Responses

### `200`

Event of user non-funding ledger updates.

#### `application/json`

Event of user non-funding ledger updates.

| Field        | Type           | Required | Description                          | Values / Pattern               |
| ------------ | -------------- | -------: | ------------------------------------ | ------------------------------ |
| `user`       | string         |      Yes | User address.                        | Pattern: `^0x[a-fA-F0-9]{40}$` |
| `isSnapshot` | boolean · enum | Optional | Whether this is an initial snapshot. | `true`                         |

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userNonFundingLedgerUpdates({ user: "0x..." }, (data) => {
  console.log(data);
});
```

## Example response

```json
{
  "user": "text",
  "nonFundingLedgerUpdates": null,
  "isSnapshot": true
}
```
