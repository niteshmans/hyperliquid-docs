# userRole

**POST** `/info`

Request user role.

## Body

`application/json`

### Request user role

* `type` — `undefined` · enum · Required\
  Type of request.\
  Possible values: `userRole`
* `user` — `string` · min: 42 · max: 42 · Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

User role.

`application/json`

User role.

```json
{
  "role": "missing"
}
```

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

const data = await client.userRole({ user: "0x..." });
```
