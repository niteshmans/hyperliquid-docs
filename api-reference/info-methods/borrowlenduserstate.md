# borrowLendUserState

`POST /info`

Request borrow/lend user state.

## Body

```json
{
  "type": "borrowLendUserState",
  "user": "0x..."
}
```

* `type` — undefined · enum · Required
  * Possible values: `borrowLendUserState`
* `user` — string · min: 42 · max: 42 · Required
  * Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

User's borrow/lend state.

* `tokenToState` — any\[]\[] · Required
  * Array of tuples of token IDs and their borrow/lend state.
* `health` — string · enum · Required
  * Possible values: `healthy`
* `healthFactor` — any · nullable · Required

```json
{
  "tokenToState": [
    []
  ],
  "health": "healthy",
  "healthFactor": null
}
```

### 422

Failed to deserialize the JSON body into the target type

### 500

Internal Server Error

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.borrowLendUserState({ user: "0x..." });
```
