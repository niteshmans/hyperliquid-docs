# delegatorSummary

Request user's staking summary.

## Body

`application/json`

Request user's staking summary.

* `type` — enum, required\
  Type of request.\
  Possible values: `delegatorSummary`
* `user` — string, required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`\
  Min: 42\
  Max: 42

## Responses

### `200`

User's staking summary.

`application/json`

* `delegated` — string, required\
  Total amount of delegated tokens.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `undelegated` — string, required\
  Total amount of undelegated tokens.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `totalPendingWithdrawal` — string, required\
  Total amount of tokens pending withdrawal.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `nPendingWithdrawals` — number, required\
  Number of pending withdrawals.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.delegatorSummary({ user: "0x..." });
```

## Test it

### `200`

User's staking summary.

```json
{
  "delegated": "text",
  "undelegated": "text",
  "totalPendingWithdrawal": "text",
  "nPendingWithdrawals": 1
}
```
