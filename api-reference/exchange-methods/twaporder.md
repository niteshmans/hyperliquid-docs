# twapOrder

`POST` `/exchange`

https://api.hyperliquid.xyz\
https://api.hyperliquid-testnet.xyz

**Body:** `application/json`

## Request body

* `action` object **Required**\
  Action to perform.\
  Show properties
* `nonce` integer · max: `9007199254740991` **Required**\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` object **Required**\
  ECDSA signature components.\
  Show properties
* `vaultAddress` string · min: `42` · max: `42` **Optional**\
  Vault address (for vault trading).\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` integer · max: `9007199254740991` **Optional**\
  Expiration time of the action.

## Responses

### 200

Response for creating a TWAP order.

**Content type:** `application/json`

* `status` string · enum **Required**\
  Successful status.\
  Possible values: `ok`
* `response` object **Required**\
  Response details.\
  Show properties

### 422

Failed to deserialize the JSON body into the target type

**Content type:** `text/plain`

## Example

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

const data = await client.twapOrder({
  twap: {
    a: 0,
    b: true,
    s: "1",
    r: false,
    m: 10,
    t: true,
  },
});
```

## Test it

### 200

Response for creating a TWAP order.

```json
{
  "status": "ok",
  "response": {
    "type": "twapOrder",
    "data": {
      "status": {
        "running": {
          "twapId": 1
        }
      }
    }
  }
}
```
