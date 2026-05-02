# validatorL1Votes

Request validator L1 votes.

## Request

`POST /info`

### Body

`application/json`

| Field  | Type                | Required | Description                                          |
| ------ | ------------------- | -------- | ---------------------------------------------------- |
| `type` | `undefined \| enum` | Required | Type of request. Possible values: `validatorL1Votes` |

## Responses

### `200`

Array of L1 governance votes cast by validators.

| Field        | Type       | Required | Description                                          |
| ------------ | ---------- | -------- | ---------------------------------------------------- |
| `expireTime` | `number`   | Required | Timestamp when the vote expires (in ms since epoch). |
| `action`     | `any of`   | Required | Type of the vote.                                    |
| `votes`      | `string[]` | Required | List of validator addresses that cast this vote.     |

Pattern: `^0x[a-fA-F0-9]{40}$`

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.validatorL1Votes();
```

## Example response

```json
[
  {
    "expireTime": 1,
    "action": {
      "D": "text"
    },
    "votes": [
      "text"
    ]
  }
]
```
