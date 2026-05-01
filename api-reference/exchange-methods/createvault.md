# createVault

`POST /exchange`

Create a vault.

## Body

`application/json`

| Field          | Type                            | Required | Description                                             |
| -------------- | ------------------------------- | -------- | ------------------------------------------------------- |
| `action`       | object                          | Yes      | Action to perform.                                      |
| `nonce`        | integer · max: 9007199254740991 | Yes      | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature`    | object                          | Yes      | ECDSA signature components.                             |
| `expiresAfter` | integer · max: 9007199254740991 | No       | Expiration time of the action.                          |

## Responses

### 200

Response for creating a vault.

```json
{
  "status": "ok",
  "response": {
    "type": "createVault",
    "data": "text"
  }
}
```

### 422

Failed to deserialize the JSON body into the target type.

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

const data = await client.createVault({
  name: "...",
  description: "...",
  initialUsd: 100 * 1e6,
  nonce: Date.now(),
});
```
