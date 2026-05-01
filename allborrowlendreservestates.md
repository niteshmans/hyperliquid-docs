# allBorrowLendReserveStates

Request all borrow/lend reserve states.

## Body

`application/json`

Type of request.

* `type` — **required** enum
  * Possible values: `allBorrowLendReserveStates`

## Responses

### `200`

Array of tuples of reserve IDs and their borrow/lend reserve state.

`application/json`

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

const data = await client.allBorrowLendReserveStates();
```

## Test it

`200`

Array of tuples of reserve IDs and their borrow/lend reserve state.

```json
[
  []
]
```
