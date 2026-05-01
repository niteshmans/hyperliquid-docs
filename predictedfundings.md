# predictedFundings

Request predicted funding rates.

## Body

`application/json`

* `type` — `undefined · enum` — Required\
  Type of request.\
  Possible values: `predictedFundings`

## Responses

* `200` — Array of tuples of asset symbols and their predicted funding data.
* `422` — Failed to deserialize the JSON body into the target type
* `500` — Internal Server Error

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.predictedFundings();
```

## Test it

`200`

Array of tuples of asset symbols and their predicted funding data.

```json
[
  []
]
```
