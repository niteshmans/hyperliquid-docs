# perpDexLimits

`POST /info`

Request builder deployed perpetual market limits.

## Body

`application/json`

| Field  | Type   | Required | Description                                       |
| ------ | ------ | -------- | ------------------------------------------------- |
| `type` | enum   | Required | Type of request. Possible values: `perpDexLimits` |
| `dex`  | string | Required | DEX name (empty string for main dex).             |

## Responses

### 200

Builder deployed perpetual market limits.

```json
{
  "totalOiCap": "text",
  "oiSzCapPerPerp": "text",
  "maxTransferNtl": "text",
  "coinToOiCap": [\
    []\
  ]
}
```

### 422

Failed to deserialize the JSON body into the target type

### 500

Internal Server Error

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.perpDexLimits({ dex: "test" });
```
