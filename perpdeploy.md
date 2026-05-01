# perpDeploy

`POST /exchange`

Base URLs:

* Mainnet: `https://api.hyperliquid.xyz`
* Testnet: `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

| Field          | Type                              | Required | Description                                             |
| -------------- | --------------------------------- | -------- | ------------------------------------------------------- |
| `action`       | one of                            | Yes      | Action to perform.                                      |
| `nonce`        | integer · max: `9007199254740991` | Yes      | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature`    | object                            | Yes      | ECDSA signature components.                             |
| `expiresAfter` | integer · max: `9007199254740991` | No       | Expiration time of the action.                          |

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` optional

Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.perpDeploy({
  registerAsset: {
    maxGas: 1000000,
    assetRequest: {
      coin: "USDC",
      szDecimals: 8,
      oraclePx: "1",
      marginTableId: 1,
      onlyIsolated: false,
    },
    dex: "test",
    schema: null,
  },
});
```
