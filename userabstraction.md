# userAbstraction

Request user abstraction state.

## Body

`application/json`

| Field  | Type                         | Required | Description                                         |
| ------ | ---------------------------- | -------- | --------------------------------------------------- |
| `type` | `undefined · enum`           | Required | Type of request. Possible values: `userAbstraction` |
| `user` | `string · min: 42 · max: 42` | Required | User address. Pattern: `^0[xX][0-9a-fA-F]+$`        |

## Responses

### `200`

User abstraction state.

`application/json`

Possible values:

* `unifiedAccount`
* `portfolioMargin`
* `disabled`
* `default`
* `dexAbstraction`

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

const data = await client.userAbstraction({ user: "0x..." });
```

## Test it

### `200`

User abstraction state.

```
unifiedAccount
```
