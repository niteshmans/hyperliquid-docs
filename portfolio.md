# portfolio

Request user portfolio.

## Body

`application/json`

* `type` — enum, required\
  Type of request.
  * Possible values: `portfolio`
* `user` — string, required\
  User address.
  * Min: `42`
  * Max: `42`
  * Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Portfolio metrics grouped by time periods.

`application/json`

* `items` — any, optional

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

const data = await client.portfolio({ user: "0x..." });
```

## Test it

### `200`

Portfolio metrics grouped by time periods.

```json
[]
```
