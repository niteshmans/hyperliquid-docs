# convertToMultiSigUser

`POST /exchange`

Convert a single-signature account to a multi-signature account or vice versa.

## Body

`application/json`

Convert a single-signature account to a multi-signature account or vice versa.

* `action` **object** — Required. Action to perform.
* `nonce` **integer** · max: `9007199254740991` — Required. Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` **object** — Required. ECDSA signature components.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` — Optional

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.convertToMultiSigUser({
  signers: {
    authorizedUsers: ["0x...", "0x...", "0x..."],
    threshold: 2,
  },
});
```
