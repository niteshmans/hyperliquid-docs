# subAccountTransfer

Transfer between sub-accounts (perpetual).

## Body

`application/json`

*   `action` `object` **Required**\
    Action to perform.

    Show properties
* `nonce` `integer` · max: `9007199254740991` **Required**\
  Nonce (timestamp in ms) used to prevent replay attacks.
*   `signature` `object` **Required**\
    ECDSA signature components.

    Show properties
* `expiresAfter` `integer` · max: `9007199254740991` **Optional**\
  Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` **Optional**\
  Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.subAccountTransfer({
  subAccountUser: "0x...",
  isDeposit: true,
  usd: 1 * 1e6,
});
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
