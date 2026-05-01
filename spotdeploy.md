# spotDeploy

Deploying HIP-1 and HIP-2 assets.

## Body

`application/json`

| Field          | Required | Description                                             |
| -------------- | -------- | ------------------------------------------------------- |
| `action`       | one of   | Action to perform.                                      |
| `nonce`        | Required | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature`    | Required | ECDSA signature components.                             |
| `expiresAfter` | Optional | Expiration time of the action.                          |

## Responses

### `200`

Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.spotDeploy({
  registerToken2: {
    spec: {
      name: "USDC",
      szDecimals: 8,
      weiDecimals: 8,
    },
    maxGas: 1000000,
    fullName: "USD Coin",
  },
});
```
