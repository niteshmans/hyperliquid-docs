# maxMarketOrderNtls

Request maximum market order notionals.

## Body

**Content-Type:** `application/json`

### `type` · enum · Required

Type of request.

Possible values:

* `maxMarketOrderNtls`

## Responses

### `200`

Array of tuples containing maximum market order notionals and their corresponding asset symbols.

**Content-Type:** `application/json`

`items`: any · Optional

### `422`

Failed to deserialize the JSON body into the target type

**Content-Type:** `text/plain`

### `500`

Internal Server Error

**Content-Type:** `application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.maxMarketOrderNtls();
```

## Test it

### `200`

Array of tuples containing maximum market order notionals and their corresponding asset symbols.

```json
[\
  []\
]
```
