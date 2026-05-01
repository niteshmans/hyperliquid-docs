# spotClearinghouseState

`POST /info`

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

Request spot clearinghouse state.

## Body

`application/json`

* `type` undefined · enum · Required
  * Type of request.
  * Possible values: `spotClearinghouseState`
* `user` string · min: 42 · max: 42 · Required
  * User address.
  * Pattern: `^0[xX][0-9a-fA-F]+$`
* `dex` string · Optional
  * DEX name (empty string for main dex).

## Responses

### 200

Account summary for spot trading.

`application/json`

* `balances` object\[] · Required
  * Array of available token balances.
* `evmEscrows` object\[] · Optional
  * Array of escrowed balances.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.spotClearinghouseState({ user: "0x..." });
```

## Test it

### 200

Account summary for spot trading.

```json
{
  "balances": [
    {
      "coin": "text",
      "token": 1,
      "total": "text",
      "hold": "text",
      "entryNtl": "text"
    }
  ],
  "evmEscrows": [
    {
      "coin": "text",
      "token": 1,
      "total": "text"
    }
  ]
}
```
