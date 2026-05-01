# perpDexStatus

`POST /info`

Request perp DEX status.

## Body

`application/json`

| Field  | Type               | Required | Description                                                                                   |
| ------ | ------------------ | -------- | --------------------------------------------------------------------------------------------- |
| `type` | `undefined · enum` | Required | Type of request. Possible values: `perpDexStatus`                                             |
| `dex`  | `string`           | Required | Perp dex name of builder-deployed dex market. The empty string represents the first perp dex. |

## Responses

### `200`

Status of a perp DEX.

`application/json`

| Field             | Type     | Required | Description        |
| ----------------- | -------- | -------- | ------------------ |
| `totalNetDeposit` | `string` | Required | Total net deposit. |

Pattern: `^[0-9]+(\.[0-9]+)?$`

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

const data = await client.perpDexStatus({ dex: "test" });
```

## Test it

### `200`

Status of a perp DEX.

```json
{
  "totalNetDeposit": "text"
}
```
