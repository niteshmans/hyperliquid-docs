# vaultModify

`POST /exchange`

Modify a vault's configuration.

## Body

`application/json`

* `action` (object, required) — Action to perform.
* `nonce` (integer, max: 9007199254740991, required) — Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` (object, required) — ECDSA signature components.
* `expiresAfter` (integer, max: 9007199254740991, optional) — Expiration time of the action.

## Responses

### 200

Successful response without specific data or error response.

`application/json`

`any` (optional)

Successful response without specific data or error response.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.vaultModify({
  vaultAddress: "0x...",
  allowDeposits: true,
  alwaysCloseOnWithdraw: false,
});
```

## Test it

```
No content
```
