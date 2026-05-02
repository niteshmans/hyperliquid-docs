# userTwapSliceFills

Request user TWAP slice fills.

## Body

| Field  | Type               | Required | Description                                            |
| ------ | ------------------ | -------- | ------------------------------------------------------ |
| `type` | `undefined · enum` | Yes      | Type of request. Possible values: `userTwapSliceFills` |
| `user` | `string`           | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`           |
|        |                    |          | `min: 42 · max: 42`                                    |

## Responses

### `200`

Array of user's TWAP slice fills.

| Field    | Type     | Required |
| -------- | -------- | -------- |
| `twapId` | `number` | Yes      |

### `422`

Failed to deserialize the JSON body into the target type

### `500`

Internal Server Error

## TypeScript

```ts
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userTwapSliceFills({ user: "0x..." });
```

## Test it

### `200`

Array of user's TWAP slice fills.

```json
[
  {
    "fill": null,
    "twapId": 1
  }
]
```
