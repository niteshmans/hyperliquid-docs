# scheduleCancel

Schedule a cancel-all operation at a future time.

## Body

`application/json`

| Field          | Type    | Required | Description                                                       |
| -------------- | ------- | -------- | ----------------------------------------------------------------- |
| `action`       | object  | Yes      | Action to perform.                                                |
| `nonce`        | integer | Yes      | Nonce (timestamp in ms) used to prevent replay attacks.           |
| `signature`    | object  | Yes      | ECDSA signature components.                                       |
| `vaultAddress` | string  | No       | Vault address (for vault trading). Pattern: `^0[xX][0-9a-fA-F]+$` |
| `expiresAfter` | integer | No       | Expiration time of the action.                                    |

## Responses

### 200

Successful response without specific data or error response.

`application/json`

`any`

### 422

Failed to deserialize the JSON body into the target type.

`text/plain`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.scheduleCancel({ time: Date.now() + 10_000 });
```

## Test it

### 200

Successful response without specific data or error response.

```
No content
```
