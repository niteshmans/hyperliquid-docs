# spotMeta

Request spot trading metadata.

## Body

`application/json`

### Fields

*   `type` — `undefined · enum` — Required\
    Type of request.

    Possible values: `spotMeta`

## Responses

### `200`

Metadata for spot assets.

#### Response body

* `universe` — `object[]` — Required\
  Trading universes available for spot trading.
* `tokens` — `object[]` — Required\
  Tokens available for spot trading.

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

### `500`

Internal Server Error.

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.spotMeta();
```

## Test it

### `200`

Metadata for spot assets.

```json
{
  "universe": [
    {
      "tokens": [
        1
      ],
      "name": "text",
      "index": 1,
      "isCanonical": true
    }
  ],
  "tokens": [
    {
      "name": "text",
      "szDecimals": 1,
      "weiDecimals": 1,
      "index": 1,
      "tokenId": "text",
      "isCanonical": true,
      "evmContract": {
        "address": "text",
        "evm_extra_wei_decimals": 1
      },
      "fullName": "text",
      "deployerTradingFeeShare": "text"
    }
  ]
}
```
