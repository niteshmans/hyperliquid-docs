# vaultTransfer

Deposit or withdraw from a vault.

## Body

`application/json`

* `action` **object** — Required\
  Action to perform.
* `nonce` **integer** `max: 9007199254740991` — Required\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` **object** — Required\
  ECDSA signature components.
* `expiresAfter` **integer** `max: 9007199254740991` — Optional\
  Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` — Optional\
  Successful response without specific data or error response.

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

await client.vaultTransfer({
  vaultAddress: "0x...",
  isDeposit: true,
  usd: 10 * 1e6,
});
```
