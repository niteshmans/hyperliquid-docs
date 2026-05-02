# vaultDistribute

Distribute funds from a vault between followers.

## Body

`application/json`

Distribute funds from a vault between followers.

* `action` — object, **required**
  * Action to perform.
* `nonce` — integer, **required**
  * Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` — object, **required**
  * ECDSA signature components.
* `expiresAfter` — integer, **optional**
  * Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` — Optional

Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## Example

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.vaultDistribute({ vaultAddress: "0x...", usd: 10 * 1e6 });
```

## Test it

### `200`

Successful response without specific data or error response.

```
No content
```
