# agentSetAbstraction

Set User abstraction mode (method for agent wallet).

## Body

`application/json`

* `action` — object — Required\
  Action to perform.
* `nonce` — integer · max: 9007199254740991 — Required\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` — object — Required\
  ECDSA signature components.
* `expiresAfter` — integer · max: 9007199254740991 — Optional\
  Expiration time of the action.

## Responses

* `200` — Successful response without specific data or error response.\
  `application/json`\
  `any` — Optional
* `422` — Failed to deserialize the JSON body into the target type\
  `text/plain`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.agentSetAbstraction({ abstraction: "u" });
```

## Test it

```
No content
```
