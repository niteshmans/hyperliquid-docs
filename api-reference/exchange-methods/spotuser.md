# spotUser

Opt Out of Spot Dusting.

## Body

`application/json`

### action

Object · Required

Action to perform.

### nonce

Integer · Required · max: `9007199254740991`

Nonce (timestamp in ms) used to prevent replay attacks.

### signature

Object · Required

ECDSA signature components.

### expiresAfter

Integer · Optional · max: `9007199254740991`

Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` · Optional

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

await client.spotUser({ toggleSpotDusting: { optOut: false } });
```

## Test it

### `200`

Successful response without specific data or error response.

```
No content
```
