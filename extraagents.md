# extraAgents

Request user extra agents.

## Body

`application/json`

| Field  | Type   | Required | Description                                     |
| ------ | ------ | -------- | ----------------------------------------------- |
| `type` | enum   | Yes      | Type of request. Possible values: `extraAgents` |
| `user` | string | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`    |

## Responses

### `200`

Array of extra agent details for a user.

```json
[
  {
    "address": "text",
    "name": "text",
    "validUntil": 1
  }
]
```

| Field        | Type   | Required | Description                                         |
| ------------ | ------ | -------- | --------------------------------------------------- |
| `address`    | string | Yes      | Extra agent address. Pattern: `^0x[a-fA-F0-9]{40}$` |
| `name`       | string | Yes      | Extra agent name.                                   |
| `validUntil` | number | Yes      | Validity period as a timestamp (in ms since epoch). |

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

const data = await client.extraAgents({ user: "0x..." });
```
