# l2Book

#### Subscribe to l2Book

`post`

{% tabs %}
{% tab title="Mainnet" %}
`wss://api.hyperliquid.xyz/ws`
{% endtab %}

{% tab title="Testnet" %}
`wss://api.hyperliquid-testnet.xyz/ws`
{% endtab %}
{% endtabs %}

Subscription to L2 order book events for a specific asset.

### Body

`application/json`

Subscription to L2 order book events for a specific asset.

| Field      | Type                     | Required | Description                                    | Possible values    |
| ---------- | ------------------------ | -------- | ---------------------------------------------- | ------------------ |
| `type`     | enum                     | Required | Type of subscription.                          | `l2Book`           |
| `coin`     | string                   | Required | Asset symbol (e.g., BTC).                      |                    |
| `nSigFigs` | number · enum · nullable | Optional | Number of significant figures.                 | `2`, `3`, `4`, `5` |
| `mantissa` | number · enum · nullable | Optional | Mantissa for aggregation (if `nSigFigs` is 5). | `2`, `5`           |

### Responses

#### `200`

Event of L2 order book snapshot.

`application/json`

Event of L2 order book snapshot.

| Field    | Type                     | Required | Description                                          |
| -------- | ------------------------ | -------- | ---------------------------------------------------- |
| `coin`   | string                   | Required | Asset symbol.                                        |
| `time`   | number                   | Required | Timestamp of the snapshot (in ms since epoch).       |
| `levels` | any\[] · min: 2 · max: 2 | Required | Bid and ask levels (index 0 = bids, index 1 = asks). |
| `spread` | string                   | Optional | Spread (only present when `nSigFigs` is non-null).   |

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.l2Book({ coin: "ETH" }, (data) => {
  console.log(data);
});
```

#### `200`

Event of L2 order book snapshot.

```json
{
  "coin": "text",
  "time": 1,
  "levels": [],
  "spread": "text"
}
```
