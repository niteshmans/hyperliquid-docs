# userRateLimit

`POST /info`

Request user rate limits.

## Body

`application/json`

* `type` — `undefined · enum` — Required\
  Type of request. Possible values: `userRateLimit`
* `user` — `string · min: 42 · max: 42` — Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

User rate limits.

`application/json`

* `cumVlm` — `string` — Required\
  Cumulative trading volume.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `nRequestsUsed` — `number` — Required\
  Number of API requests used.
* `nRequestsCap` — `number` — Required\
  Maximum allowed API requests.
* `nRequestsSurplus` — `number` — Required\
  Number of surplus API requests.

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

const data = await client.userRateLimit({ user: "0x..." });
```

## Test it

### `200`

User rate limits.

```json
{
  "cumVlm": "text",
  "nRequestsUsed": 1,
  "nRequestsCap": 1,
  "nRequestsSurplus": 1
}
```
