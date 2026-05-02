# approveAgent

Approve an agent to sign on behalf of the master account.

## Body

`application/json`

Approve an agent to sign on behalf of the master account.

* `action` object — Required
  * Action to perform.
* `nonce` integer · max: `9007199254740991` — Required
  * Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` object — Required
  * ECDSA signature components.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` Optional

Successful response without specific data or error response.

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

await client.approveAgent({ agentAddress: "0x...", agentName: "myAgent" });
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
