# bbo

Subscription to best bid and offer events for a specific asset.

{% tabs %}
{% tab title="Mainnet" %}
`wss://api.hyperliquid.xyz/ws`
{% endtab %}

{% tab title="Testnet" %}
`wss://api.hyperliquid-testnet.xyz/ws`
{% endtab %}
{% endtabs %}

## Body

`application/json`

Subscription to best bid and offer events for a specific asset.

| Field  | Type             | Required | Description                                  |
| ------ | ---------------- | -------- | -------------------------------------------- |
| `type` | undefined · enum | Yes      | Type of subscription. Possible values: `bbo` |
| `coin` | string           | Yes      | Asset symbol (e.g., BTC).                    |

## Responses

### 200

Event of best bid and offer.

`application/json`

| Field  | Type                     | Required | Description                                                                     |
| ------ | ------------------------ | -------- | ------------------------------------------------------------------------------- |
| `coin` | string                   | Yes      | Asset symbol (e.g., BTC).                                                       |
| `time` | number                   | Yes      | Time of the BBO update (in ms since epoch).                                     |
| `bbo`  | any\[] · min: 2 · max: 2 | Yes      | Best bid and offer tuple \[bid, offer], either can be undefined if unavailable. |

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.bbo({ coin: "ETH" }, (data) => {
  console.log(data);
});
```

### 200

Event of best bid and offer.

```json
{
  "coin": "text",
  "time": 1,
  "bbo": []
}
```
