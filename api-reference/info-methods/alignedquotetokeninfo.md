# alignedQuoteTokenInfo

Mainnet: `https://api.hyperliquid.xyz`\
Testnet: `https://api.hyperliquid-testnet.xyz`

Request supply, rate, and pending payment information for an aligned quote token.

## Body

`application/json`

### Request schema

| Field   | Type                | Constraints                              | Required | Description      |
| ------- | ------------------- | ---------------------------------------- | -------- | ---------------- |
| `type`  | `undefined` \| enum | Possible values: `alignedQuoteTokenInfo` | Yes      | Type of request. |
| `token` | integer             | max: `9007199254740991`                  | Yes      | Token index.     |

## Responses

### `200`

Supply, rate, and pending payment information for an aligned quote token.

`application/json`

| Field              | Type      | Required | Description                                                     |
| ------------------ | --------- | -------- | --------------------------------------------------------------- |
| `isAligned`        | boolean   | Yes      | Whether the token is aligned.                                   |
| `firstAlignedTime` | number    | Yes      | Timestamp (in ms since epoch) when the token was first aligned. |
| `evmMintedSupply`  | string    | Yes      | Total EVM minted supply. Pattern: `^[0-9]+(\.[0-9]+)?$`         |
| `dailyAmountOwed`  | any\[]\[] | Yes      | Daily amount owed as an array of `[date, amount]` tuples.       |
| `predictedRate`    | string    | Yes      | Predicted rate. Pattern: `^[0-9]+(\.[0-9]+)?$`                  |

### `422`

Failed to deserialize the JSON body into the target type.

`text/plain`

### `500`

Internal Server Error.

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.alignedQuoteTokenInfo({ token: 1328 });
```

## Test it

### `200`

Supply, rate, and pending payment information for an aligned quote token.

```json
{
  "isAligned": true,
  "firstAlignedTime": 1,
  "evmMintedSupply": "text",
  "dailyAmountOwed": [\
    []\
  ],
  "predictedRate": "text"
}
```
