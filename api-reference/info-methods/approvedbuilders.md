# approvedBuilders

Request approved builders for a user.

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

| Field  | Type                         | Required | Description                                          |
| ------ | ---------------------------- | -------- | ---------------------------------------------------- |
| `type` | `undefined · enum`           | Yes      | Type of request. Possible values: `approvedBuilders` |
| `user` | `string · min: 42 · max: 42` | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`         |

## Responses

| Status | Description                                              | Content Type       | Body       |
| ------ | -------------------------------------------------------- | ------------------ | ---------- |
| `200`  | Array of approved builder addresses.                     | `application/json` | `string[]` |
| `422`  | Failed to deserialize the JSON body into the target type | `text/plain`       |            |
| `500`  | Internal Server Error                                    | `application/json` |            |

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.approvedBuilders({ user: "0x..." });
```

## Test it

```json
[
  "text"
]
```
