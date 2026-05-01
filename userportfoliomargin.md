# userPortfolioMargin

Enable/disable user portfolio margin.

**Base URLs**

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

Enable/disable user portfolio margin.

| Field       | Type                            | Required | Description                                             |
| ----------- | ------------------------------- | -------- | ------------------------------------------------------- |
| `action`    | object                          | Required | Action to perform.                                      |
| `nonce`     | integer · max: 9007199254740991 | Required | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature` | object                          | Required | ECDSA signature components.                             |

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` Optional

Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.userPortfolioMargin({ user: "0x...", enabled: true });
```
