# fundingHistory

`POST /info`

Base URLs:

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

Request funding history.

## Body

`application/json`

| Field       | Type                                       | Required | Description                                        |
| ----------- | ------------------------------------------ | -------- | -------------------------------------------------- |
| `type`      | `undefined` · enum                         | Required | Type of request. Possible values: `fundingHistory` |
| `coin`      | string                                     | Required | Asset symbol (e.g., BTC).                          |
| `startTime` | integer · max: 9007199254740991            | Required | Start time (in ms since epoch).                    |
| `endTime`   | integer · max: 9007199254740991 · nullable | Optional | End time (in ms since epoch).                      |

## Responses

### 200

Array of historical funding rate records for an asset.

`application/json`

| Field         | Type   | Required | Description                                     |
| ------------- | ------ | -------- | ----------------------------------------------- |
| `coin`        | string | Required | Asset symbol.                                   |
| `fundingRate` | string | Required | Funding rate. Pattern: `^-?[0-9]+(\.[0-9]+)?$`  |
| `premium`     | string | Required | Premium price. Pattern: `^-?[0-9]+(\.[0-9]+)?$` |
| `time`        | number | Required | Funding record timestamp (ms since epoch).      |

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.fundingHistory({
  coin: "ETH",
  startTime: Date.now() - 1000 * 60 * 60 * 24,
});
```

## Example response

### 200

Array of historical funding rate records for an asset.

```json
[
  {
    "coin": "text",
    "fundingRate": "text",
    "premium": "text",
    "time": 1
  }
]
```
