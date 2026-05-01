# subAccountSpotTransfer

**POST** `/exchange`

Transfer between sub-accounts (spot).

## Body

`application/json`

* `action` — object, required
  * Action to perform.
* `nonce` — integer, max: `9007199254740991`, required
  * Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` — object, required
  * ECDSA signature components.
* `expiresAfter` — integer, max: `9007199254740991`, optional
  * Expiration time of the action.

## Responses

* `200` — Successful response without specific data or error response.
  * `application/json`
  * any, optional
* `422` — Failed to deserialize the JSON body into the target type
  * `text/plain`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.subAccountSpotTransfer({
  subAccountUser: "0x...",
  isDeposit: true,
  token: "USDC:0xeb62eee3685fc4c43992febcd9e75443",
  amount: "1",
});
```
