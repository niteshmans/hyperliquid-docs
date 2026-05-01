# userFunding

Request array of user funding ledger updates.

## Body

`application/json`

| Field       | Type            | Required | Description                     | Constraints                                      |
| ----------- | --------------- | -------- | ------------------------------- | ------------------------------------------------ |
| `type`      | enum            | Yes      | Type of request.                | Possible values: `userFunding`                   |
| `user`      | string          | Yes      | User address.                   | Min: 42, max: 42, pattern: `^0[xX][0-9a-fA-F]+$` |
| `startTime` | integer \| null | No       | Start time (in ms since epoch). | Max: `9007199254740991`                          |
| `endTime`   | integer \| null | No       | End time (in ms since epoch).   | Max: `9007199254740991`                          |

## Responses

### 200

Array of user funding ledger updates.

`application/json`

| Field   | Type   | Required | Description                                  | Constraints                    |
| ------- | ------ | -------- | -------------------------------------------- | ------------------------------ |
| `time`  | number | Yes      | Timestamp of the update (in ms since epoch). |                                |
| `hash`  | string | Yes      | L1 transaction hash.                         | Pattern: `^0x[a-fA-F0-9]{64}$` |
| `delta` | object | Yes      | Update details.                              |                                |

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userFunding({ user: "0x..." });
```

## Example response

```json
[
  {
    "time": 1,
    "hash": "text",
    "delta": {
      "type": "funding",
      "coin": "text",
      "usdc": "text",
      "szi": "text",
      "fundingRate": "text",
      "nSamples": 1
    }
  }
]
```
