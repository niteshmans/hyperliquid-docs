# leadingVaults

Request leading vaults for a user.

## Body

**Content type:** `application/json`

| Field  | Type                                    | Constraints                      | Description      |
| ------ | --------------------------------------- | -------------------------------- | ---------------- |
| `type` | `undefined` · enum · Required           | Possible values: `leadingVaults` | Type of request. |
| `user` | `string` · min: 42 · max: 42 · Required | Pattern: `^0[xX][0-9a-fA-F]+$`   | User address.    |

## Responses

### `200`

Array of leading vaults for a user.

**Content type:** `application/json`

| Field     | Type                | Constraints                    | Description    |
| --------- | ------------------- | ------------------------------ | -------------- |
| `address` | `string` · Required | Pattern: `^0x[a-fA-F0-9]{40}$` | Vault address. |
| `name`    | `string` · Required |                                | Vault name.    |

### `422`

Failed to deserialize the JSON body into the target type.

**Content type:** `text/plain`

### `500`

Internal Server Error.

**Content type:** `application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.leadingVaults({ user: "0x..." });
```

## Example response

```json
[
  {
    "address": "text",
    "name": "text"
  }
]
```
