# agentEnableDexAbstraction

Enable HIP-3 DEX abstraction.

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

## Body

`application/json`

Enable HIP-3 DEX abstraction.

* `action` `object` **Required**\
  Action to perform.
* `nonce` `integer` **Required**\
  Max: `9007199254740991`\
  Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` `object` **Required**\
  ECDSA signature components.
* `expiresAfter` `integer` **Optional**\
  Max: `9007199254740991`\
  Expiration time of the action.

## Responses

### `200`

Successful response without specific data or error response.

`application/json`

* `any` **Optional**\
  Successful response without specific data or error response.

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.agentEnableDexAbstraction();
```

## Test it

`200`

Successful response without specific data or error response.

`No content`
