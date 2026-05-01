# validatorSummaries

`POST /info`

## Endpoints

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

## Request

Request validator summaries.

### Body

`application/json`

| Field  | Type               | Required | Description                                            |
| ------ | ------------------ | -------- | ------------------------------------------------------ |
| `type` | `undefined · enum` | Yes      | Type of request. Possible values: `validatorSummaries` |

## Responses

### `200`

Array of validator performance statistics.

`application/json`

Each item in the array has the following properties:

| Field             | Type                | Required | Description                                                              |
| ----------------- | ------------------- | -------- | ------------------------------------------------------------------------ |
| `validator`       | `string`            | Yes      | Address of the validator. Pattern: `^0x[a-fA-F0-9]{40}$`                 |
| `signer`          | `string`            | Yes      | Address of the validator signer. Pattern: `^0x[a-fA-F0-9]{40}$`          |
| `name`            | `string`            | Yes      | Name of the validator.                                                   |
| `description`     | `string`            | Yes      | Description of the validator.                                            |
| `nRecentBlocks`   | `number`            | Yes      | Number of blocks produced recently.                                      |
| `stake`           | `number`            | Yes      | Total amount of tokens staked **(unsafe integer)**.                      |
| `isJailed`        | `boolean`           | Yes      | Whether the validator is currently jailed.                               |
| `unjailableAfter` | `number · nullable` | Yes      | Timestamp when the validator can be unjailed (in ms since epoch).        |
| `isActive`        | `boolean`           | Yes      | Whether the validator is currently active.                               |
| `commission`      | `string`            | Yes      | Commission rate charged by the validator. Pattern: `^[0-9]+(\.[0-9]+)?$` |
| `stats`           | `any[]`             | Yes      | Performance statistics over different time periods. Min: 3, Max: 3       |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## Test it

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.validatorSummaries();
```

### `200`

Array of validator performance statistics.

```json
[
  {
    "validator": "text",
    "signer": "text",
    "name": "text",
    "description": "text",
    "nRecentBlocks": 1,
    "stake": 1,
    "isJailed": true,
    "unjailableAfter": 1,
    "isActive": true,
    "commission": "text",
    "stats": []
  }
]
```
