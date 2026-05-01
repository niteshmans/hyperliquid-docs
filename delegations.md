# delegations

Request user staking delegations.

## Body

`application/json`

| Field  | Type               | Required | Description                                     |
| ------ | ------------------ | -------- | ----------------------------------------------- |
| `type` | `undefined` · enum | Yes      | Type of request. Possible values: `delegations` |
| `user` | `string`           | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`    |

## Responses

### `200`

Array of user's delegations to validators.

`application/json`

| Field                  | Type     | Required | Description                                                                 |
| ---------------------- | -------- | -------- | --------------------------------------------------------------------------- |
| `validator`            | `string` | Yes      | Validator address. Pattern: `^0x[a-fA-F0-9]{40}$`                           |
| `amount`               | `string` | Yes      | Amount of tokens delegated to the validator. Pattern: `^[0-9]+(\.[0-9]+)?$` |
| `lockedUntilTimestamp` | `number` | Yes      | Locked until timestamp (in ms since epoch).                                 |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.delegations({ user: "0x..." });
```

## Test it

### `200`

Array of user's delegations to validators.

```json
[
  {
    "validator": "text",
    "amount": "text",
    "lockedUntilTimestamp": 1
  }
]
```
