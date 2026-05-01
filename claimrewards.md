# claimRewards

`POST /exchange`

{% tabs %}
{% tab title="Mainnet" %}
`https://api.hyperliquid.xyz`
{% endtab %}

{% tab title="Testnet" %}
`https://api.hyperliquid-testnet.xyz`
{% endtab %}
{% endtabs %}

## Body

`application/json`

Claim rewards from referral program.

* `action` object **Required**
  * Action to perform.
* `nonce` integer, max: `9007199254740991` **Required**
  * Nonce (timestamp in ms) used to prevent replay attacks.
* `signature` object **Required**
  * ECDSA signature components.
* `expiresAfter` integer, max: `9007199254740991` **Optional**
  * Expiration time of the action.

## Responses

| Code | Description                                                  | Content Type       |
| ---- | ------------------------------------------------------------ | ------------------ |
| 200  | Successful response without specific data or error response. | `application/json` |
| 422  | Failed to deserialize the JSON body into the target type     | `text/plain`       |

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.claimRewards();
```

## Test it

`200`

Successful response without specific data or error response.

```
No content
```
