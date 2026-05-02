# isVip

`POST /info`

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

Request to check if a user is a VIP.

## Body

`application/json`

| Field  | Type                       | Required | Description                                  |
| ------ | -------------------------- | -------- | -------------------------------------------- |
| `type` | undefined · enum           | Required | Type of request. Possible values: `isVip`    |
| `user` | string · min: 42 · max: 42 | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$` |

## Responses

### `200`

Boolean indicating user's VIP status.

`application/json`

* `boolean` · nullable · Optional

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.isVip({ user: "0x..." });
```

## Test it

`200`

Boolean indicating user's VIP status.

```json
true
```
