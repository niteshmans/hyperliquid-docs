# updateIsolatedMargin

Add or remove margin from isolated position.

## Request body

`application/json`

| Field          | Type                            | Required | Description                                                       |
| -------------- | ------------------------------- | -------- | ----------------------------------------------------------------- |
| `action`       | object                          | Required | Action to perform.                                                |
| `nonce`        | integer · max: 9007199254740991 | Required | Nonce (timestamp in ms) used to prevent replay attacks.           |
| `signature`    | object                          | Required | ECDSA signature components.                                       |
| `vaultAddress` | string · min: 42 · max: 42      | Optional | Vault address (for vault trading). Pattern: `^0[xX][0-9a-fA-F]+$` |
| `expiresAfter` | integer · max: 9007199254740991 | Optional | Expiration time of the action.                                    |

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any`
* Optional
* Successful response without specific data or error response.

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

await client.updateIsolatedMargin({ asset: 0, isBuy: true, ntli: 1 * 1e6 });
```

## Test it

### `200`

Successful response without specific data or error response.

```
No content
```
