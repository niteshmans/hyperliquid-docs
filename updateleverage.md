# updateLeverage

Update cross or isolated leverage on a coin.

## Body

`application/json`

| Field          | Type                              | Required | Description                                                       |
| -------------- | --------------------------------- | -------: | ----------------------------------------------------------------- |
| `action`       | object                            |      Yes | Action to perform.                                                |
| `nonce`        | integer · max: `9007199254740991` |      Yes | Nonce (timestamp in ms) used to prevent replay attacks.           |
| `signature`    | object                            |      Yes | ECDSA signature components.                                       |
| `vaultAddress` | string · min: `42` · max: `42`    |       No | Vault address (for vault trading). Pattern: `^0[xX][0-9a-fA-F]+$` |
| `expiresAfter` | integer · max: `9007199254740991` |       No | Expiration time of the action.                                    |

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` Optional

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

## Example

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.updateLeverage({ asset: 0, isCross: true, leverage: 5 });
```
