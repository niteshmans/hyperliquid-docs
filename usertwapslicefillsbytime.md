# userTwapSliceFillsByTime

`POST /info`

Request user TWAP slice fills by time.

## Body

`application/json`

| Field             | Type                                         | Required | Description                                                                                |
| ----------------- | -------------------------------------------- | -------- | ------------------------------------------------------------------------------------------ |
| `type`            | `undefined` · enum                           | Yes      | Type of request. Possible values: `userTwapSliceFillsByTime`                               |
| `user`            | `string` · min: 42 · max: 42                 | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`                                               |
| `startTime`       | `integer` · max: 9007199254740991            | Yes      | Start time (in ms since epoch).                                                            |
| `endTime`         | `integer` · max: 9007199254740991 · nullable | Optional | End time (in ms since epoch).                                                              |
| `aggregateByTime` | `boolean`                                    | Optional | If true, partial fills are aggregated when a crossing order fills multiple resting orders. |

## Responses

### `200`

Array of user's TWAP slice fill by time.

`application/json`

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userTwapSliceFillsByTime({
  user: "0x...",
  startTime: Date.now() - 1000 * 60 * 60 * 24,
});
```
