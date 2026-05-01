# userFillsByTime

Request array of user fills by time.

## Request

`POST /info`

### Body

`application/json`

| Field             | Type                                                    | Required | Description                                                                                |
| ----------------- | ------------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------ |
| `type`            | `undefined · enum`                                      | Required | Type of request. Possible values: `userFillsByTime`                                        |
| `user`            | `string · min: 42 · max: 42`                            | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`                                               |
| `startTime`       | `integer · max: 9007199254740991`                       | Required | Start time (in ms since epoch).                                                            |
| `endTime`         | `any of` / `integer · max: 9007199254740991 · nullable` | Optional | End time (in ms since epoch).                                                              |
| `aggregateByTime` | `boolean`                                               | Optional | If true, partial fills are aggregated when a crossing order fills multiple resting orders. |
| `reversed`        | `boolean`                                               | Optional | If true, fills are returned in reverse chronological order (newest first).                 |

## Responses

### `200`

Array of user trade fills by time.

`application/json`

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

const data = await client.userFillsByTime({
  user: "0x...",
  startTime: Date.now() - 1000 * 60 * 60 * 24,
});
```

## Test it

200

Array of user trade fills by time.
