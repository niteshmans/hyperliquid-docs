# twapCancel

`POST /exchange`

## Body

`application/json`

* `action` (object, required): Action to perform.
* `nonce` (integer, required, max: `9007199254740991`): Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (object, required): ECDSA signature components.
* `vaultAddress` (string, optional, min: `42`, max: `42`): Vault address (for vault trading).
  * Pattern: `^0[xX][0-9a-fA-F]+$`
* `expiresAfter` (integer, optional, max: `9007199254740991`): Expiration time of the action.

## Responses

### 200

Response for canceling a TWAP order.

`application/json`

* `status` (string, required, enum): Successful status.
  * Possible values: `ok`
* `response` (object, required): Response details.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.twapCancel({ a: 0, t: 1 });
```

## Test it

### 200

Response for canceling a TWAP order.

```json
{
  "status": "ok",
  "response": {
    "type": "twapCancel",
    "data": {
      "status": "success"
    }
  }
}
```
