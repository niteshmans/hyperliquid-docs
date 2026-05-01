# webData2

Request comprehensive user and market data.

## Body

`application/json`

| Field  | Type   | Required | Description      | Constraints / Values                                                                           |
| ------ | ------ | -------: | ---------------- | ---------------------------------------------------------------------------------------------- |
| `type` | enum   |      Yes | Type of request. | Possible values: `webData2`                                                                    |
| `user` | string |      Yes | User address.    | <p>Min: <code>42</code>, Max: <code>42</code><br>Pattern: <code>^0[xX][0-9a-fA-F]+$</code></p> |

## Responses

### `200`

Comprehensive user and market data.

| Field                 | Type                   | Required | Description                                             | Constraints / Values           |
| --------------------- | ---------------------- | -------: | ------------------------------------------------------- | ------------------------------ |
| `totalVaultEquity`    | string                 |      Yes | Total equity in vaults.                                 | Pattern: `^[0-9]+(\.[0-9]+)?$` |
| `agentAddress`        | string \| null         |      Yes | Agent address if one exists.                            | Pattern: `^0x[a-fA-F0-9]{40}$` |
| `agentValidUntil`     | number \| null         |      Yes | Timestamp until which the agent is valid.               |                                |
| `cumLedger`           | string                 |      Yes | Cumulative ledger value.                                | Pattern: `^[0-9]+(\.[0-9]+)?$` |
| `assetCtxs`           | `PerpAssetCtxSchema[]` |      Yes | Array of contexts for each perpetual asset.             |                                |
| `serverTime`          | number                 |      Yes | Server timestamp (in ms since epoch).                   |                                |
| `isVault`             | boolean                |      Yes | Whether this account is a vault.                        |                                |
| `user`                | string                 |      Yes | User address.                                           | Pattern: `^0x[a-fA-F0-9]{40}$` |
| `twapStates`          | `any[][]`              |      Yes | Array of tuples containing TWAP order ID and its state. |                                |
| `spotAssetCtxs`       | `SpotAssetCtxSchema[]` |      Yes | Asset context for each spot asset.                      |                                |
| `optOutOfSpotDusting` | boolean                | Optional | Whether the user has opted out of spot dusting.         | Possible values: `true`        |

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

const data = await client.webData2({ user: "0x..." });
```

## Test it

### `200`

Comprehensive user and market data.

```json
{
  "clearinghouseState": null,
  "leadingVaults": null,
  "totalVaultEquity": "text",
  "openOrders": null,
  "agentAddress": "text",
  "agentValidUntil": 1,
  "cumLedger": "text",
  "meta": null,
  "assetCtxs": [],
  "serverTime": 1,
  "isVault": true,
  "user": "text",
  "twapStates": [
    []
  ],
  "spotState": null,
  "spotAssetCtxs": [],
  "optOutOfSpotDusting": true,
  "perpsAtOpenInterestCap": null
}
```
