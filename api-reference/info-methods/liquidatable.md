# liquidatable

`POST /info`

Request liquidatable.

## Body

`application/json`

| Field | Type             | Required | Description      | Possible values |
| ----- | ---------------- | -------- | ---------------- | --------------- |
| type  | undefined · enum | Required | Type of request. | `liquidatable`  |

## Responses

### 200

Response for liquidatable request.

`application/json`

`items` any Optional

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.liquidatable();
```

## Test it

200

Response for liquidatable request.

```json
[]
```
