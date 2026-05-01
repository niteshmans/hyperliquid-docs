# userBorrowLendInterest

Request user borrow/lend interest.

## Body

**Content type:** `application/json`

| Field       | Type                | Required | Description                     | Constraints                                          |
| ----------- | ------------------- | -------- | ------------------------------- | ---------------------------------------------------- |
| `type`      | `undefined \| enum` | Yes      | Type of request.                | Possible values: `userBorrowLendInterest`            |
| `user`      | `string`            | Yes      | User address.                   | min: `42`, max: `42`, pattern: `^0[xX][0-9a-fA-F]+$` |
| `startTime` | `integer`           | Yes      | Start time (in ms since epoch). | max: `9007199254740991`                              |
| `endTime`   | `integer`           | Optional | End time (in ms since epoch).   | max: `9007199254740991`, nullable                    |

## Responses

### `200`

User's borrow/lend interest.

**Content type:** `application/json`

| Field    | Type     | Required | Description                                  | Constraints                    |
| -------- | -------- | -------- | -------------------------------------------- | ------------------------------ |
| `time`   | `number` | Yes      | Timestamp of the update (in ms since epoch). |                                |
| `token`  | `string` | Yes      | Token symbol.                                |                                |
| `borrow` | `string` | Yes      | Borrow interest amount.                      | pattern: `^[0-9]+(\.[0-9]+)?$` |
| `supply` | `string` | Yes      | Supply interest amount.                      | pattern: `^[0-9]+(\.[0-9]+)?$` |

### `422`

Failed to deserialize the JSON body into the target type.

**Content type:** `text/plain`

### `500`

Internal Server Error.

**Content type:** `application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userBorrowLendInterest({
  user: "0x...",
  startTime: Date.now() - 1000 * 60 * 60 * 24,
});
```

## Test it

### `200`

User's borrow/lend interest.

```json
[
  {
    "time": 1,
    "token": "text",
    "borrow": "text",
    "supply": "text"
  }
]
```
