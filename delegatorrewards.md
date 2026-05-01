# delegatorRewards

**Base URL**

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

Request user staking rewards.

## Body

`application/json`

| Field  | Type               | Required | Description                                          |
| ------ | ------------------ | -------- | ---------------------------------------------------- |
| `type` | `undefined · enum` | Yes      | Type of request. Possible values: `delegatorRewards` |
| `user` | `string`           | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`         |

## Responses

### `200`

Array of rewards received from staking activities.

`application/json`

| Field         | Type            | Required | Description                                                      |
| ------------- | --------------- | -------- | ---------------------------------------------------------------- |
| `time`        | `number`        | Yes      | Timestamp when the reward was received (in ms since epoch).      |
| `source`      | `string · enum` | Yes      | Source of the reward. Possible values: `delegation` `commission` |
| `totalAmount` | `string`        | Yes      | Total reward amount. Pattern: `^[0-9]+(\.[0-9]+)?$`              |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.delegatorRewards({ user: "0x..." });
```

## Test it

### `200`

Array of rewards received from staking activities.

```json
[
  {
    "time": 1,
    "source": "delegation",
    "totalAmount": "text"
  }
]
```
