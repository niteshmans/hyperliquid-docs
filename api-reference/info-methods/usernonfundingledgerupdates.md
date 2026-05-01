# userNonFundingLedgerUpdates

Request user non-funding ledger updates.

https://api.hyperliquid.xyz\
https://api.hyperliquid-testnet.xyz

## Body

`application/json`

### Request body

* `type` `undefined` · enum · Required\
  Type of request.\
  Possible values: `userNonFundingLedgerUpdates`
* `user` `string` · min: 42 · max: 42 · Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `startTime` `integer` · max: 9007199254740991 · Optional\
  Start time (in ms since epoch).
* `endTime` `integer` · max: 9007199254740991 · nullable · Optional\
  End time (in ms since epoch).

## Responses

### `200`

Array of user's non-funding ledger update.

`application/json`

Each item includes:

* `time` `number` · Required\
  Timestamp of the update (in ms since epoch).
* `hash` `string` · Required\
  L1 transaction hash.\
  Pattern: `^0x[a-fA-F0-9]{64}$`
* `delta` `any of` · Required\
  Update details.

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

const data = await client.userNonFundingLedgerUpdates({ user: "0x..." });
```

## Test it

### `200`

Array of user's non-funding ledger update.

```json
[
  {
    "time": 1,
    "hash": "text",
    "delta": {
      "type": "accountClassTransfer",
      "usdc": "text",
      "toPerp": true
    }
  }
]
```
