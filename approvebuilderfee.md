# approveBuilderFee

`POST /exchange`

## Endpoints

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

Approve a maximum fee rate for a builder.

*   `action` object **Required**\
    Action to perform.

    Show propertiesplus
* `nonce` integer · max: `9007199254740991` **Required**\
  Nonce (timestamp in ms) used to prevent replay attacks.
*   `signature` object **Required**\
    ECDSA signature components.

    Show propertiesplus

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` Optional\
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

await client.approveBuilderFee({ maxFeeRate: "0.01%", builder: "0x..." });
```

## Test it

### `200`

Successful response without specific data or error response.

```
No content
```
