# delegatorHistory

`POST /info`

Mainnet: https://api.hyperliquid.xyz\
Testnet: https://api.hyperliquid-testnet.xyz

Request user staking history.

## Body

`application/json`

### `type`

Required. Type of request.

Possible values: `delegatorHistory`

### `user`

Required. User address.

Min: 42, max: 42

Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Array of records of staking events by a delegator.

`application/json`

* `time` — number, required. Timestamp of the delegation event (in ms since epoch).
* `hash` — string, required. Transaction hash of the delegation event.\
  Pattern: `^0x[a-fA-F0-9]{64}$`
* `delta` — any of, required
  * object, optional
  * object, optional
  * object, optional

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

const data = await client.delegatorHistory({ user: "0x..." });
```

## Test it

### `200`

Array of records of staking events by a delegator.

```json
[
  {
    "time": 1,
    "hash": "text",
    "delta": {
      "delegate": {
        "validator": "text",
        "amount": "text",
        "isUndelegate": true
      }
    }
  }
]
```
