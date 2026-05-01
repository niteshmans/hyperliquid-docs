# userDexAbstraction

Enable/disable HIP-3 DEX abstraction.

## Body

`application/json`

* `action` (`object`, required) — Action to perform.
* `nonce` (`integer`, max: `9007199254740991`, required) — Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (`object`, required) — ECDSA signature components.

## Responses

* `200` — Successful response without specific data or error response.
  * `application/json`
  * `any` — Optional
* `422` — Failed to deserialize the JSON body into the target type.
  * `text/plain`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.userDexAbstraction({ user: "0x...", enabled: true });
```
