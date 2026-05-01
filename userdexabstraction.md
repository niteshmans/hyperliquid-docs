# userDexAbstraction

Request user HIP-3 DEX abstraction state.

## Body

`application/json`

| Field  | Type                         | Required | Description                                            |
| ------ | ---------------------------- | -------- | ------------------------------------------------------ |
| `type` | `undefined` · enum           | Required | Type of request. Possible values: `userDexAbstraction` |
| `user` | `string` · min: 42 · max: 42 | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`           |

## Responses

### `200`

User HIP-3 DEX abstraction state.

`application/json`

`boolean` · nullable · Optional

User HIP-3 DEX abstraction state.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userDexAbstraction({ user: "0x..." });
```

## Test it

### `200`

User HIP-3 DEX abstraction state.

```json
true
```
