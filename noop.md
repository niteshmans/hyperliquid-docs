# noop

This action does not do anything (no operation), but causes the nonce to be marked as used.

## Base URLs

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

### Properties

* `action` (object, required) — Action to perform.
* `nonce` (integer, required, max: `9007199254740991`) — Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (object, required) — ECDSA signature components.
* `expiresAfter` (integer, optional, max: `9007199254740991`) — Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` — Optional

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.noop();
```

## Test it

### `200`

Successful response without specific data or error response.

`No content`
