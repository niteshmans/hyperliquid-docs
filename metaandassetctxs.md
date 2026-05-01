# metaAndAssetCtxs

Request metadata and asset contexts.

## Body

`application/json`

| Field  | Type               | Required | Description                           | Possible values    |
| ------ | ------------------ | -------- | ------------------------------------- | ------------------ |
| `type` | `undefined` · enum | Required | Type of request.                      | `metaAndAssetCtxs` |
| `dex`  | string             | Optional | DEX name (empty string for main dex). |                    |

## Responses

### `200`

Tuple containing metadata and array of asset contexts.

`application/json`

* items: any (Optional)

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.metaAndAssetCtxs();
```

## Test it

`200`

Tuple containing metadata and array of asset contexts.

```json
[]
```
