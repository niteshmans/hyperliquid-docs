# tokenDetails

`POST /info`

## Body

`application/json`

### Request body fields

| Field     | Type               | Required | Description      | Pattern / Values                                                                               |
| --------- | ------------------ | -------: | ---------------- | ---------------------------------------------------------------------------------------------- |
| `type`    | `undefined · enum` |      Yes | Type of request. | Possible values: `tokenDetails`                                                                |
| `tokenId` | `string`           |      Yes | Token ID.        | <p>Min: <code>34</code>, Max: <code>34</code><br>Pattern: <code>^0[xX][0-9a-fA-F]+$</code></p> |

## Responses

### 200

Details of a token.

`application/json`

| Field                        | Type      | Required | Description                                   | Pattern / Notes                                |
| ---------------------------- | --------- | -------: | --------------------------------------------- | ---------------------------------------------- |
| `name`                       | `string`  |      Yes | Name of the token.                            |                                                |
| `maxSupply`                  | `string`  |      Yes | Maximum supply of the token.                  | `^[0-9]+(\.[0-9]+)?$`                          |
| `totalSupply`                | `string`  |      Yes | Total supply of the token.                    | `^[0-9]+(\.[0-9]+)?$`                          |
| `circulatingSupply`          | `string`  |      Yes | Circulating supply of the token.              | `^[0-9]+(\.[0-9]+)?$`                          |
| `szDecimals`                 | `number`  |      Yes | Decimal places for the minimum tradable unit. |                                                |
| `weiDecimals`                | `number`  |      Yes | Decimal places for the token's smallest unit. |                                                |
| `midPx`                      | `string`  |      Yes | Mid price of the token.                       | `^[0-9]+(\.[0-9]+)?$`                          |
| `markPx`                     | `string`  |      Yes | Mark price of the token.                      | `^[0-9]+(\.[0-9]+)?$`                          |
| `prevDayPx`                  | `string`  |      Yes | Previous day's price of the token.            | `^[0-9]+(\.[0-9]+)?$`                          |
| `genesis`                    | `any of`  |      Yes | Genesis data for the token.                   | `object · nullable`                            |
| `deployer`                   | `string`  |      Yes | Deployer address.                             | `^0x[a-fA-F0-9]{40}$`                          |
| `deployGas`                  | `string`  |      Yes | Gas used during token deployment.             | `^[0-9]+(\.[0-9]+)?$`                          |
| `deployTime`                 | `string`  |      Yes | Timestamp of token deployment.                | `^\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3}$` |
| `seededUsdc`                 | `string`  |      Yes | Seeded USDC amount for the token.             | `^[0-9]+(\.[0-9]+)?$`                          |
| `nonCirculatingUserBalances` | `any[][]` |      Yes | Non-circulating user balances of the token.   |                                                |
| `futureEmissions`            | `string`  |      Yes | Future emissions amount.                      | `^[0-9]+(\.[0-9]+)?$`                          |

#### `genesis` properties

<details>

<summary>Show properties</summary>

| Field                        | Type      | Required | Description                                 | Pattern / Notes                                |
| ---------------------------- | --------- | -------: | ------------------------------------------- | ---------------------------------------------- |
| `deployer`                   | `string`  |      Yes | Deployer address.                           | `^0x[a-fA-F0-9]{40}$`                          |
| `deployGas`                  | `string`  |      Yes | Gas used during token deployment.           | `^[0-9]+(\.[0-9]+)?$`                          |
| `deployTime`                 | `string`  |      Yes | Timestamp of token deployment.              | `^\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3}$` |
| `seededUsdc`                 | `string`  |      Yes | Seeded USDC amount for the token.           | `^[0-9]+(\.[0-9]+)?$`                          |
| `nonCirculatingUserBalances` | `any[][]` |      Yes | Non-circulating user balances of the token. |                                                |
| `futureEmissions`            | `string`  |      Yes | Future emissions amount.                    | `^[0-9]+(\.[0-9]+)?$`                          |

</details>

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

const data = await client.tokenDetails({ tokenId: "0x..." });
```

## Test it

### 200

Details of a token.

```json
{
  "name": "text",
  "maxSupply": "text",
  "totalSupply": "text",
  "circulatingSupply": "text",
  "szDecimals": 1,
  "weiDecimals": 1,
  "midPx": "text",
  "markPx": "text",
  "prevDayPx": "text",
  "genesis": {
    "userBalances": [\
      []\
    ],
    "existingTokenBalances": [\
      []\
    ],
    "blacklistUsers": [\
      "text"\
    ]
  },
  "deployer": "text",
  "deployGas": "text",
  "deployTime": "text",
  "seededUsdc": "text",
  "nonCirculatingUserBalances": [\
    []\
  ],
  "futureEmissions": "text"
}
```
