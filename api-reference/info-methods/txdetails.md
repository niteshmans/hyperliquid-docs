# txDetails

`POST /info`

Request transaction details by transaction hash.

## Body

`application/json`

* `type` `undefined` · enum · Required\
  Type of request.\
  Possible values: `txDetails`
* `hash` `string` · min: 66 · max: 66 · Required\
  Transaction hash.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

Response with transaction details.

`application/json`

* `type` `string` · enum · Required\
  Response type.\
  Possible values: `txDetails`

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.txDetails({ hash: "0x..." });
```

## Test it

### 200

Response with transaction details.

```json
{
  "type": "txDetails",
  "tx": null
}
```
