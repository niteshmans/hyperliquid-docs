# historicalOrders

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz

`/info`
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz

`/info`
{% endtab %}
{% endtabs %}

Request user historical orders.

## Body

`application/json`

Request user historical orders.

| Field  | Type                         | Required | Description                                          |
| ------ | ---------------------------- | -------- | ---------------------------------------------------- |
| `type` | `undefined · enum`           | Yes      | Type of request. Possible values: `historicalOrders` |
| `user` | `string · min: 42 · max: 42` | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`         |

## Responses

### 200

Array of frontend orders with current processing status.

`application/json`

Array of frontend orders with current processing status.

| Field             | Type     | Required | Description                                                     |
| ----------------- | -------- | -------- | --------------------------------------------------------------- |
| `statusTimestamp` | `number` | Yes      | Timestamp when the status was last updated (in ms since epoch). |

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.historicalOrders({ user: "0x..." });
```

## Test it

### 200

Array of frontend orders with current processing status.

```json
[
  {
    "order": null,
    "status": null,
    "statusTimestamp": 1
  }
]
```
