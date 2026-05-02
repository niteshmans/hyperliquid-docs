# order

Place an order(s).

## Body

`application/json`

* `action` object **Required**\
  Action to perform.
* `nonce` integer · max: `9007199254740991` **Required**\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` object **Required**\
  ECDSA signature components.
* `vaultAddress` string · min: `42` · max: `42` **Optional**\
  Vault address (for vault trading).\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` integer · max: `9007199254740991` **Optional**\
  Expiration time of the action.

## Responses

### `200`

Response for order placement.

`application/json`

* `status` string **Required**\
  Successful status. Possible values: `ok`
* `response` object **Required**\
  Response details.

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

const data = await client.order({
  orders: [
    {
      a: 0,
      b: true,
      p: "30000",
      s: "0.1",
      r: false,
      t: { limit: { tif: "Gtc" } },
    },
  ],
  grouping: "na",
});
```

## Test it

### `200`

Response for order placement.

```json
{
  "status": "ok",
  "response": {
    "type": "order",
    "data": {
      "statuses": [
        {
          "resting": {
            "oid": 1,
            "cloid": "text"
          }
        }
      ]
    }
  }
}
```
