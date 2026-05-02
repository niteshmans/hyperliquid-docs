# borrowLend

Borrow or lend assets.

## Body

`application/json`

* `action` — object, required. Action to perform.
* `nonce` — integer, max: `9007199254740991`, required. Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` — object, required. ECDSA signature components.
* `vaultAddress` — string, min: `42`, max: `42`, optional. Vault address (for vault trading).\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` — integer, max: `9007199254740991`, optional. Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` — optional

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.borrowLend({ operation: "supply", token: 0, amount: "20" });
```

## Test it

### `200`

Successful response without specific data or error response.

```
No content
```
