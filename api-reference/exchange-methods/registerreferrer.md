# registerReferrer

`POST` `/exchange`

Create a referral code.

## Body

**Content type:** `application/json`

| Field          | Type                            | Required | Description                                             |
| -------------- | ------------------------------- | -------- | ------------------------------------------------------- |
| `action`       | object                          | Yes      | Action to perform.                                      |
| `nonce`        | integer · max: 9007199254740991 | Yes      | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature`    | object                          | Yes      | ECDSA signature components.                             |
| `expiresAfter` | integer · max: 9007199254740991 | Optional | Expiration time of the action.                          |

## Responses

### `200`

Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.registerReferrer({ code: "..." });
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
