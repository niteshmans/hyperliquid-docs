# perpDexs

Request all perpetual dexs.

## Base URLs

* `https://api.hyperliquid.xyz`
* `https://api.hyperliquid-testnet.xyz`

## Request body

`application/json`

### `type` · undefined · enum · Required

Type of request.

Possible values: `perpDexs`

## Responses

### `200`

Array of perpetual dexes (null is main dex).

`application/json`

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.perpDexs();
```

## Test it

### `200`

Array of perpetual dexes (null is main dex).

```json
[
  {
    "name": "text",
    "fullName": "text",
    "deployer": "text",
    "oracleUpdater": "text",
    "feeRecipient": "text",
    "assetToStreamingOiCap": [
      []
    ],
    "subDeployers": [
      []
    ],
    "deployerFeeScale": "text",
    "lastDeployerFeeScaleChangeTime": "text",
    "assetToFundingMultiplier": [
      []
    ],
    "assetToFundingInterestRate": [
      []
    ]
  }
]
```
