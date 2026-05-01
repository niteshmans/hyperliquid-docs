# topUpIsolatedOnlyMargin

Top up isolated margin by targeting a specific leverage.

## Body

`application/json`

*   `action` object **Required**\
    Action to perform.

    Show properties
* `nonce` integer · max: `9007199254740991` **Required**\
  Nonce (timestamp in ms) used to prevent replay attacks.
*   `signature` object **Required**\
    ECDSA signature components.

    Show properties
*   `vaultAddress` string · min: `42` · max: `42` **Optional**\
    Vault address (for vault trading).

    Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` integer · max: `9007199254740991` **Optional**\
  Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

```
No content
```

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## Example

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.topUpIsolatedOnlyMargin({ asset: 0, leverage: "0.5" });
```
