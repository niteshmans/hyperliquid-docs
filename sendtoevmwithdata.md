# sendToEvmWithData

Transfer tokens from Core to EVM with an additional data payload for `ICoreReceiveWithData` contracts.

## Body

`application/json`

* `action` object **Required**\
  Action to perform.
* `nonce` integer · max: `9007199254740991` **Required**\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` object **Required**\
  ECDSA signature components.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

`any` Optional

Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.sendToEvmWithData({
  token: "USDC",
  amount: "1",
  sourceDex: "spot",
  destinationRecipient: "0x...",
  addressEncoding: "hex",
  destinationChainId: 42161,
  gasLimit: 200000,
  data: "0x",
});
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
