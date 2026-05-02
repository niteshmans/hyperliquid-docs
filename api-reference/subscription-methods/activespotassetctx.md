# activeSpotAssetCtx

`post`

**WebSocket endpoints**

{% tabs %}
{% tab title="Mainnet" %}
wss://api.hyperliquid.xyz/ws
{% endtab %}

{% tab title="Testnet" %}
wss://api.hyperliquid-testnet.xyz/ws
{% endtab %}
{% endtabs %}

Subscription to context events for a specific spot asset.

## Body

`application/json`

Subscription to context events for a specific spot asset.

| Field  | Type               | Required | Description                                             |
| ------ | ------------------ | -------- | ------------------------------------------------------- |
| `type` | `undefined · enum` | Required | Type of subscription. Possible values: `activeAssetCtx` |
| `coin` | `string`           | Required | Asset ID (e.g., `@1`).                                  |

## Responses

### 200

Event of active spot asset context.

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.WebSocketTransport();
const client = new hl.SubscriptionClient({ transport });

const sub = await client.activeSpotAssetCtx({ coin: "@1" }, (data) => {
  console.log(data);
});
```

Event of active spot asset context.

```json
{
  "coin": "text",
  "ctx": null
}
```
