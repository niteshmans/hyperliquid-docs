# usdClassTransfer

`post /exchange`

Transfer funds between Spot account and Perp account.

## Body

`application/json`

* `action` (object, required) — Action to perform.
* `nonce` (integer, max: 9007199254740991, required) — Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (object, required) — ECDSA signature components.

## Responses

* `200` — Successful response without specific data or error response.
* `422` — Failed to deserialize the JSON body into the target type.

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.usdClassTransfer({ amount: "1", toPerp: true });
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
