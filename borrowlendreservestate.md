# borrowLendReserveState

Request borrow/lend reserve states.

## Body

`application/json`

### Request body

* `type` — **required**. Type of request.
  * Possible values: `borrowLendReserveState`
* `token` — **required**. Token index.

## Responses

### `200`

Borrow/lend reserve state.

`application/json`

* `borrowYearlyRate` — Borrow interest rate (yearly).
* `supplyYearlyRate` — Supply interest rate (yearly).
* `balance` — Reserve balance.
* `utilization` — Reserve utilization ratio.
* `oraclePx` — Oracle price.
* `ltv` — Loan-to-value (LTV) ratio.
* `totalSupplied` — Total supplied amount.
* `totalBorrowed` — Total borrowed amount.

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

const data = await client.borrowLendReserveState({ token: 0 });
```

## Test it

### `200`

Borrow/lend reserve state.

```json
{
  "borrowYearlyRate": "text",
  "supplyYearlyRate": "text",
  "balance": "text",
  "utilization": "text",
  "oraclePx": "text",
  "ltv": "text",
  "totalSupplied": "text",
  "totalBorrowed": "text"
}
```
