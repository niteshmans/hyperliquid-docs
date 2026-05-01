# userFundings

`post`

Subscription to user funding events for a specific user.

## Body

`application/json`

* `type` `undefined · enum` — Required\
  Type of subscription.\
  Possible values: `userFundings`
* `user` `string · min: 42 · max: 42` — Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Event of user fundings.

`application/json`

* `user` `string` — Required\
  User address.\
  Pattern: `^0x[a-fA-F0-9]{40}$`
* `fundings` `object[]` — Required\
  Array of user funding ledger updates.
  * `time`
  * `coin`
  * `usdc`
  * `szi`
  * `fundingRate`
  * `nSamples`
* `isSnapshot` `boolean · enum` — Optional\
  Whether this is an initial snapshot.\
  Possible values: `true`

## Example request

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.userFundings({ user: "0x..." }, (data) => {
  console.log(data);
});
```

## Example response

```json
{
  "user": "text",
  "fundings": [
    {
      "time": 1,
      "coin": "text",
      "usdc": "text",
      "szi": "text",
      "fundingRate": "text",
      "nSamples": 1
    }
  ],
  "isSnapshot": true
}
```
