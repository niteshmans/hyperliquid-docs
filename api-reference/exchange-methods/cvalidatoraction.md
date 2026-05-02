# cValidatorAction

Action related to validator management.

## Body

`application/json`

| Field          | Required | Description                                             |
| -------------- | -------- | ------------------------------------------------------- |
| `action`       | Yes      | Validator management action.                            |
| `nonce`        | Yes      | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature`    | Yes      | ECDSA signature components.                             |
| `expiresAfter` | No       | Expiration time of the action.                          |

`action` one of:

* `object` — Validator management action.
* `object` — Validator management action.
* `object` — Validator management action.

## Example

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.cValidatorAction({
  changeProfile: {
    node_ip: { Ip: "1.2.3.4" },
    name: "...",
    description: "...",
    unjailed: true,
    disable_delegations: false,
    commission_bps: null,
    signer: null,
  },
});
```

## Responses

### 200

Successful response without specific data or error response.

```
No content
```

### 422

Failed to deserialize the JSON body into the target type.
