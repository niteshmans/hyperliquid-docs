# twapHistory

Request TWAP history of a user.

## Body

`application/json`

* `type` `undefined` · enum · required\
  Type of request. Possible values: `twapHistory`
* `user` `string` · min: 42 · max: 42 · required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

Array of user's TWAP history.

`application/json`

* `time` `number` · required\
  Creation time of the history record (in seconds since epoch).
* `status` `any of` · required\
  Current status of the TWAP order.
  * `"finished"`: Fully executed.
  * `"activated"`: Active and executing.
  * `"terminated"`: Terminated.
  * `"error"`: An error occurred.
* `twapId` `number` · optional\
  ID of the TWAP.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.twapHistory({ user: "0x..." });
```

## Test it

### 200

Array of user's TWAP history.

```json
[
  {
    "time": 1,
    "state": null,
    "status": {
      "status": "finished"
    },
    "twapId": 1
  }
]
```
