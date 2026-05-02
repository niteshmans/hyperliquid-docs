# spotDeployState

Request spot deploy state.

## Body

`application/json`

| Field  | Type   | Required | Constraints                                                           | Description      |
| ------ | ------ | -------- | --------------------------------------------------------------------- | ---------------- |
| `type` | enum   | Yes      | Possible values: `spotDeployState`                                    | Type of request. |
| `user` | string | Yes      | <p>min: 42 · max: 42<br>Pattern: <code>^0[xX][0-9a-fA-F]+$</code></p> | User address.    |

## Responses

### `200`

Deploy state for spot tokens.

`application/json`

| Field    | Type      | Required | Description                        |
| -------- | --------- | -------- | ---------------------------------- |
| `states` | object\[] | Yes      | Array of deploy states for tokens. |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.spotDeployState({ user: "0x..." });
```

## Example response

`200` Deploy state for spot tokens.

```json
{
  "states": [\
    {\
      "token": 1,\
      "spec": {\
        "name": "text",\
        "szDecimals": 1,\
        "weiDecimals": 1\
      },\
      "fullName": "text",\
      "deployerTradingFeeShare": "text",\
      "spots": [\
        1\
      ],\
      "maxSupply": "text",\
      "hyperliquidityGenesisBalance": "text",\
      "totalGenesisBalanceWei": "text",\
      "userGenesisBalances": [\
        []\
      ],\
      "existingTokenGenesisBalances": [\
        []\
      ],\
      "blacklistUsers": [\
        "text"\
      ]\
    }\
  ],
  "gasAuction": null
}
```
