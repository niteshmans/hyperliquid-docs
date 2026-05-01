# userSetAbstraction

`https://api.hyperliquid.xyz`

`https://api.hyperliquid-testnet.xyz`

`/exchange`

## Body

`application/json`

### action

`object` Required

Action to perform.

### nonce

`integer · max: 9007199254740991` Required

Nonce (timestamp in ms) used to prevent replay attacks.

### signature

`object` Required

ECDSA signature components.

## Responses

### 200

Successful response without specific data or error response.

`application/json`

`any` Optional

Successful response without specific data or error response.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.userSetAbstraction({ user: "0x...", abstraction: "dexAbstraction" });
```

## Test it

### 200

Successful response without specific data or error response.

```
No content
```
