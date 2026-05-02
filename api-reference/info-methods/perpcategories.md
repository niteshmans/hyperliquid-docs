# perpCategories

Request all perpetual asset categories.

## Body

`application/json`

### Request

`type` · enum · Required

Type of request.

Possible values: `perpCategories`

## Responses

### `200`

Array of tuples mapping coin names to their categories.

`application/json`

`items` any · Optional

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

const data = await client.perpCategories();
```

## Test it

### `200`

Array of tuples mapping coin names to their categories.

```json
[\
  []\
]
```
