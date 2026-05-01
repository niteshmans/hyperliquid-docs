# spotSend

Send spot assets to another address.

## Body

`application/json`

* `action` `object` Required\
  Action to perform.
* `nonce` `integer` · max: `9007199254740991` Required\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` `object` Required\
  ECDSA signature components.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` Optional\
Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.spotSend({
  destination: "0x...",
  token: "USDC:0xeb62eee3685fc4c43992febcd9e75443",
  amount: "1",
});
```
