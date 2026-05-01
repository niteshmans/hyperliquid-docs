# perpAnnotation

**POST** `/info`

Base URLs:

* https://api.hyperliquid.xyz
* https://api.hyperliquid-testnet.xyz

Request perp annotation.

## Body

`application/json`

### Fields

* `type` — `undefined` · enum · Required\
  Type of request.\
  Possible values: `perpAnnotation`
* `coin` — `string` · Required\
  Coin symbol for the perpetual asset.

## Responses

### `200`

Perp annotation for an asset.

`application/json`

Object · nullable · Optional

```json
{
  "category": "text",
  "description": "text",
  "displayName": "text",
  "keywords": [
    "text"
  ]
}
```

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

const data = await client.perpAnnotation({ coin: "BTC" });
```
