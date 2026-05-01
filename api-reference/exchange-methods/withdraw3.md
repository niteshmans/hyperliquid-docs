# withdraw3

Initiate a withdrawal request.

## Body

`application/json`

* `action` (`object`, required) — Action to perform.
* `nonce` (`integer`, max: `9007199254740991`, required) — Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (`object`, required) — ECDSA signature components.

## Responses

| Status | Description                                                  | Content Type       |
| ------ | ------------------------------------------------------------ | ------------------ |
| `200`  | Successful response without specific data or error response. | `application/json` |
| `422`  | Failed to deserialize the JSON body into the target type     | `text/plain`       |

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.withdraw3({ destination: "0x...", amount: "1" });
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
