# reserveRequestWeight

Reserve additional rate-limited actions for a fee.

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz

/exchange
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz

/exchange
{% endtab %}
{% endtabs %}

## Body

`application/json`

| Field          | Type                           | Required | Description                                             |
| -------------- | ------------------------------ | -------- | ------------------------------------------------------- |
| `action`       | object                         | Required | Action to perform.                                      |
| `nonce`        | integer, max: 9007199254740991 | Required | Nonce (timestamp in ms) used to prevent replay attacks. |
| `signature`    | object                         | Required | ECDSA signature components.                             |
| `expiresAfter` | integer, max: 9007199254740991 | Optional | Expiration time of the action.                          |

## Responses

### 200

Successful response without specific data or error response.

`application/json`

`any` Optional

Successful response without specific data or error response.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";
import { privateKeyToAccount } from "npm:viem/accounts";

const wallet = privateKeyToAccount("0x..."); // viem or ethers
const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.ExchangeClient({ transport, wallet });

await client.reserveRequestWeight({ weight: 10 });
```

## Test it

### 200

Successful response without specific data or error response.

```
No content
```
