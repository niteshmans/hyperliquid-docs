# perpsAtOpenInterestCap

Request perpetuals at open interest cap.

## Body

`application/json`

* `type` `undefined` · enum · Required\
  Type of request.\
  Possible values: `perpsAtOpenInterestCap`
* `dex` `string` · Optional\
  DEX name (empty string for main dex).

## Responses

### 200

Array of perpetuals at open interest caps.

`application/json`

* `string[]` · Optional\
  Array of perpetuals at open interest caps.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.perpsAtOpenInterestCap();
```

## Test it

### 200

Array of perpetuals at open interest caps.

```json
[
  "text"
]
```
