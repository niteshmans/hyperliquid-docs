# batchModify

Mainnet: `https://api.hyperliquid.xyz`\
Testnet: `https://api.hyperliquid-testnet.xyz`

`POST /exchange`

Modify multiple orders.

## Body

`application/json`

* `action` — object, required\
  Action to perform.
* `nonce` — integer, required\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` — object, required\
  ECDSA signature components.
* `vaultAddress` — string, optional\
  Vault address (for vault trading).\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` — integer, optional\
  Expiration time of the action.

## Responses

### `200`

Response for order batch modifications.

`application/json`

`any` optional

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## Example

**TypeScript**

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

const data = await client.batchModify({
  modifies: [
    {
      oid: 123,
      order: {
        a: 0,
        b: true,
        p: "31000",
        s: "0.2",
        r: false,
        t: { limit: { tif: "Gtc" } },
      },
    },
  ],
});
```
