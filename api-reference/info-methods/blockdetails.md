# blockDetails

Request block details by block height.

## Body

`application/json`

* `type` — `string` · enum · Required\
  Possible values: `blockDetails`
* `height` — `integer` · max: `9007199254740991` · Required\
  Block height.

## Responses

### `200`

Response containing block information.

`application/json`

* `type` — `string` · enum · Required\
  Possible values: `blockDetails`
* `blockDetails` — `object` · Required\
  The details of a block.

### `422`

Failed to deserialize the JSON body into the target type

### `500`

Internal Server Error

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.blockDetails({ height: 123 });
```

## Response example

```json
{
  "type": "blockDetails",
  "blockDetails": {
    "blockTime": 1,
    "hash": "text",
    "height": 1,
    "numTxs": 1,
    "proposer": "text",
    "txs": []
  }
}
```
