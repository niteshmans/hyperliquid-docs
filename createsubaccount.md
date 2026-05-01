# createSubAccount

`POST /exchange`

## Body

`application/json`

Create a sub-account.

* `action` (`object`, required) — Action to perform.
  * Show properties
* `nonce` (`integer`, max: `9007199254740991`, required) — Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (`object`, required) — ECDSA signature components.
  * Show properties
* `expiresAfter` (`integer`, max: `9007199254740991`, optional) — Expiration time of the action.

## Responses

### 200

Response for creating a sub-account.

`application/json`

* `object` (optional)
  * Show properties

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

const data = await client.createSubAccount({ name: "..." });
```

## Test it

### 200

Response for creating a sub-account.

```json
{
  "status": "ok",
  "response": {
    "type": "createSubAccount",
    "data": "text"
  }
}
```
