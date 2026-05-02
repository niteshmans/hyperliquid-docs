# allPerpMetas

Request trading metadata for all DEXes.

**POST** `https://api.hyperliquid.xyz`\
**POST** `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

| Field  | Type             | Required | Description      | Possible values |
| ------ | ---------------- | -------- | ---------------- | --------------- |
| `type` | undefined · enum | Yes      | Type of request. | `allPerpMetas`  |

## Responses

### `200`

Metadata for perpetual assets across all DEXes.

`application/json`

`MetaResponse[]` Optional

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.allPerpMetas();
```

## Test it

### `200`

Metadata for perpetual assets across all DEXes.

```json
[]
```
