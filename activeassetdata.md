# activeAssetData

Request user active asset data.

## Environments

* Mainnet: `https://api.hyperliquid.xyz`
* Testnet: `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

* `type` — undefined · enum, Required. Possible values: `activeAssetData`
* `coin` — string, Required. Asset symbol (e.g., BTC).
* `user` — string · min: 42 · max: 42, Required. User address. Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

User active asset data.

`application/json`

* `user` — string, Required. User address. Pattern: `^0x[a-fA-F0-9]{40}$`
* `coin` — string, Required. Asset symbol (e.g., BTC).
* `leverage` — any of, Required
  * object, Optional
  * object, Optional
* `maxTradeSzs` — any\[] · min: 2 · max: 2, Required. Maximum trade size range `[min, max]`.
* `availableToTrade` — any\[] · min: 2 · max: 2, Required. Available to trade range `[min, max]`.
* `markPx` — string, Required. Pattern: `^[0-9]+(\.[0-9]+)?$`

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

const data = await client.activeAssetData({ user: "0x...", coin: "ETH" });
```

## Example response

```json
{
  "user": "text",
  "coin": "text",
  "leverage": {
    "type": "isolated",
    "value": 1,
    "rawUsd": "text"
  },
  "maxTradeSzs": [],
  "availableToTrade": [],
  "markPx": "text"
}
```
