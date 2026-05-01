# spotMetaAndAssetCtxs

Request spot metadata and asset contexts.

## Body

`application/json`

### `type` · enum · Required

Type of request.

Possible values:

* `spotMetaAndAssetCtxs`

## Responses

### `200`

Tuple of spot metadata and asset contexts.

`application/json`

* `items` any Optional

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.spotMetaAndAssetCtxs();
```

## Test it

### `200`

Tuple of spot metadata and asset contexts.

```json
[]
```
