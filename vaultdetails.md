# vaultDetails

Request details of a vault.

## Body

`application/json`

| Field                                   | Type                         | Required | Description                                      |
| --------------------------------------- | ---------------------------- | -------: | ------------------------------------------------ |
| `type`                                  | `undefined` · enum           |      Yes | Type of request. Possible values: `vaultDetails` |
| `vaultAddress`                          | `string` · min: 42 · max: 42 |      Yes | Vault address. Pattern: `^0[xX][0-9a-fA-F]+$`    |
| `user`                                  | `any of`                     |       No | User address.                                    |
| `string` · min: 42 · max: 42 · nullable |                              |          | User address. Pattern: `^0[xX][0-9a-fA-F]+$`     |

## Responses

### `200`

Details of a vault or null if the vault does not exist.

`application/json`

| Field                   | Type       | Required | Description                                    |
| ----------------------- | ---------- | -------: | ---------------------------------------------- |
| `name`                  | `string`   |      Yes | Vault name.                                    |
| `vaultAddress`          | `string`   |      Yes | Vault address. Pattern: `^0x[a-fA-F0-9]{40}$`  |
| `leader`                | `string`   |      Yes | Leader address. Pattern: `^0x[a-fA-F0-9]{40}$` |
| `description`           | `string`   |      Yes | Vault description.                             |
| `apr`                   | `number`   |      Yes | Annual percentage rate.                        |
| `followerState`         | `any of`   |      Yes | Current user follower state.                   |
| `object · nullable`     |            |       No | Show properties                                |
| `leaderFraction`        | `number`   |      Yes | Ownership percentage held by leader.           |
| `leaderCommission`      | `number`   |      Yes | Leader commission percentage.                  |
| `followers`             | `object[]` |      Yes | Array of vault followers. Show properties      |
| `maxDistributable`      | `number`   |      Yes | Maximum distributable amount.                  |
| `maxWithdrawable`       | `number`   |      Yes | Maximum withdrawable amount.                   |
| `isClosed`              | `boolean`  |      Yes | Vault closure status.                          |
| `allowDeposits`         | `boolean`  |      Yes | Deposit permission status.                     |
| `alwaysCloseOnWithdraw` | `boolean`  |      Yes | Position closure policy on withdrawal.         |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.vaultDetails({ vaultAddress: "0x..." });
```

## Test it

### `200`

Details of a vault or null if the vault does not exist.

```json
{
  "name": "text",
  "vaultAddress": "text",
  "leader": "text",
  "description": "text",
  "portfolio": null,
  "apr": 1,
  "followerState": {
    "user": "text",
    "vaultEquity": "text",
    "pnl": "text",
    "allTimePnl": "text",
    "daysFollowing": 1,
    "vaultEntryTime": 1,
    "lockupUntil": 1
  },
  "leaderFraction": 1,
  "leaderCommission": 1,
  "followers": [\
    {\
      "user": "text",\
      "vaultEquity": "text",\
      "pnl": "text",\
      "allTimePnl": "text",\
      "daysFollowing": 1,\
      "vaultEntryTime": 1,\
      "lockupUntil": 1\
    }\
  ],
  "maxDistributable": 1,
  "maxWithdrawable": 1,
  "isClosed": true,
  "relationship": null,
  "allowDeposits": true,
  "alwaysCloseOnWithdraw": true
}
```
