# clearinghouseState

`POST /info`

## Request

**Body:** `application/json`

Request clearinghouse state.

| Field  | Type                         | Required | Description                                            |
| ------ | ---------------------------- | -------: | ------------------------------------------------------ |
| `type` | `undefined · enum`           |      Yes | Type of request. Possible values: `clearinghouseState` |
| `user` | `string · min: 42 · max: 42` |      Yes | User address. Pattern: `^0[xX][0-9a-fA-F]+$`           |
| `dex`  | `string`                     |       No | DEX name (empty string for main dex).                  |

## Responses

### `200`

Account summary for perpetual trading.

**Content-Type:** `application/json`

#### Response body

| Field                        | Type       | Required | Description                                                                        |
| ---------------------------- | ---------- | -------: | ---------------------------------------------------------------------------------- |
| `marginSummary`              | `object`   |      Yes | Margin summary details.                                                            |
| `crossMarginSummary`         | `object`   |      Yes | Cross-margin summary details.                                                      |
| `crossMaintenanceMarginUsed` | `string`   |      Yes | Maintenance margin used for cross-margin positions. Pattern: `^[0-9]+(\.[0-9]+)?$` |
| `withdrawable`               | `string`   |      Yes | Amount available for withdrawal. Pattern: `^[0-9]+(\.[0-9]+)?$`                    |
| `assetPositions`             | `object[]` |      Yes | Array of asset positions.                                                          |
| `time`                       | `number`   |      Yes | Timestamp when data was retrieved (in ms since epoch).                             |

### `422`

Failed to deserialize the JSON body into the target type

**Content-Type:** `text/plain`

### `500`

Internal Server Error

**Content-Type:** `application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.clearinghouseState({ user: "0x..." });
```

## Test it

### `200`

Account summary for perpetual trading.

```json
{
  "marginSummary": {
    "accountValue": "text",
    "totalNtlPos": "text",
    "totalRawUsd": "text",
    "totalMarginUsed": "text"
  },
  "crossMarginSummary": {
    "accountValue": "text",
    "totalNtlPos": "text",
    "totalRawUsd": "text",
    "totalMarginUsed": "text"
  },
  "crossMaintenanceMarginUsed": "text",
  "withdrawable": "text",
  "assetPositions": [
    {
      "type": "oneWay",
      "position": {
        "coin": "text",
        "szi": "text",
        "leverage": {
          "type": "isolated",
          "value": 1,
          "rawUsd": "text"
        },
        "entryPx": "text",
        "positionValue": "text",
        "unrealizedPnl": "text",
        "returnOnEquity": "text",
        "liquidationPx": "text",
        "marginUsed": "text",
        "maxLeverage": 1,
        "cumFunding": {
          "allTime": "text",
          "sinceOpen": "text",
          "sinceChange": "text"
        }
      }
    }
  ],
  "time": 1
}
```
