# cancelByCloid

`post /exchange`

## Body

`application/json`

Cancel order(s) by cloid.

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

Response for order cancellation by cloid.

`application/json`

`any` Optional

Response for order cancellation by cloid.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.cancelByCloid({
  cancels: [
    { asset: 0, cloid: "0x..." },
  ],
});
```

## Test it

### `200`

Response for order cancellation by cloid.

```
No content
```
