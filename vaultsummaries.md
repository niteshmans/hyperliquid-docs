# vaultSummaries

`POST /info`

Request a list of vaults less than 2 hours old.

## Body

**application/json**

| Field  | Type               | Required | Description      | Possible values  |
| ------ | ------------------ | -------- | ---------------- | ---------------- |
| `type` | `undefined · enum` | Yes      | Type of request. | `vaultSummaries` |

## Responses

### 200

Array of vaults less than 2 hours old.

**application/json**

| Field              | Type      | Required | Description           | Pattern               |
| ------------------ | --------- | -------- | --------------------- | --------------------- |
| `name`             | `string`  | Yes      | Vault name.           |                       |
| `vaultAddress`     | `string`  | Yes      | Vault address.        | `^0x[a-fA-F0-9]{40}$` |
| `leader`           | `string`  | Yes      | Leader address.       | `^0x[a-fA-F0-9]{40}$` |
| `tvl`              | `string`  | Yes      | Total value locked.   | `^[0-9]+(\.[0-9]+)?$` |
| `isClosed`         | `boolean` | Yes      | Vault closure status. |                       |
| `createTimeMillis` | `number`  | Yes      | Creation timestamp.   |                       |

### 422

Failed to deserialize the JSON body into the target type

### 500

Internal Server Error

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.vaultSummaries();
```

## Test it

### 200

Array of vaults less than 2 hours old.

```json
[
  {
    "name": "text",
    "vaultAddress": "text",
    "leader": "text",
    "tvl": "text",
    "isClosed": true,
    "relationship": null,
    "createTimeMillis": 1
  }
]
```
