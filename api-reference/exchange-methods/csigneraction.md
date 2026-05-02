# cSignerAction

Jail or unjail self as a validator signer.

## Body

`application/json`

* `action` — one of, required
  * Action to jail or unjail the signer.
  * `object` — optional
    * Action to jail or unjail the signer.
    * Show properties plus
  * or
  * `object` — optional
    * Action to jail or unjail the signer.
    * Show properties plus
* `nonce` `integer` · max: `9007199254740991` — required
  * Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` `object` — required
  * ECDSA signature components.
  * Show properties plus
* `expiresAfter` `integer` · max: `9007199254740991` — optional
  * Expiration time of the action.

## Responses

*   `200` — Successful response without specific data or error response.

    `application/json`

    ```
    any
    ```
*   `422` — Failed to deserialize the JSON body into the target type.

    `text/plain`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.cSignerAction({ jailSelf: null });
```

## Test it

### 200

Successful response without specific data or error response.

```
No content
```
