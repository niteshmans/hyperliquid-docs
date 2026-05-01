# meta

Request trading metadata.

## Base URL

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

/info

## Body

`application/json`

### type

Required. Type of request.

Possible values: `meta`

### dex

Optional. DEX name (empty string for main dex).

## Responses

### 200

Metadata for perpetual assets.

* `universe` — Trading universes available for perpetual trading.
* `marginTables` — Margin requirement tables for different leverage tiers.
* `collateralToken` — Collateral token index.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.meta();
```

## 200

Metadata for perpetual assets.

```json
{
  "universe": [
    {
      "szDecimals": 1,
      "name": "text",
      "maxLeverage": 1,
      "marginTableId": 1,
      "onlyIsolated": true,
      "isDelisted": true,
      "marginMode": "strictIsolated",
      "growthMode": "enabled",
      "lastGrowthModeChangeTime": "text"
    }
  ],
  "marginTables": [
    []
  ],
  "collateralToken": 1
}
```
