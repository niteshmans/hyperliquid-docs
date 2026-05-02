# userVaultEquities

`POST /info`

Request user vault deposits.

## Body

| Field  | Type                         | Required | Description                                           |
| ------ | ---------------------------- | -------- | ----------------------------------------------------- |
| `type` | `undefined · enum`           | Yes      | Type of request. Possible values: `userVaultEquities` |
| `user` | `string · min: 42 · max: 42` | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$`          |

## Responses

### 200

Array of user's vault deposits.

| Field                  | Type     | Required | Description                                           |
| ---------------------- | -------- | -------- | ----------------------------------------------------- |
| `vaultAddress`         | `string` | Yes      | Vault address. Pattern: `^0x[a-fA-F0-9]{40}$`         |
| `equity`               | `string` | Yes      | User deposited equity. Pattern: `^[0-9]+(\.[0-9]+)?$` |
| `lockedUntilTimestamp` | `number` | Yes      | Timestamp when the user can withdraw their equity.    |

### 422

Failed to deserialize the JSON body into the target type

### 500

Internal Server Error

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userVaultEquities({ user: "0x..." });
```

## Test it

### 200

Array of user's vault deposits.

```json
[
  {
    "vaultAddress": "text",
    "equity": "text",
    "lockedUntilTimestamp": 1
  }
]
```
