# modify

`POST /exchange`

## Body

**Content type:** `application/json`

* `action` (object, required)\
  Action to perform.
* `nonce` (integer, required, max: `9007199254740991`)\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (object, required)\
  ECDSA signature components.
* `vaultAddress` (string, optional, min: `42`, max: `42`)\
  For vault trading.\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` (integer, optional, max: `9007199254740991`)\
  Expiration time of the action.

## Responses

* `200` — Successful response without specific data or error response.
* `422` — Failed to deserialize the JSON body into the target type.

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.modify({
  oid: 123,
  order: {
    a: 0,
    b: true,
    p: "31000",
    s: "0.2",
    r: false,
    t: { limit: { tif: "Gtc" } },
  },
});
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
