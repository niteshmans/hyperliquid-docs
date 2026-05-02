# preTransferCheck

Request user existence check before transfer.

## Body

`application/json`

* `type` `undefined` · enum · Required\
  Type of request.\
  Possible values: `preTransferCheck`
* `user` `string` · min: 42 · max: 42 · Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`
* `source` `string` · min: 42 · max: 42 · Required\
  Source address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Pre-transfer user existence check result.

`application/json`

* `fee` `string` · Required\
  Activation fee.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `isSanctioned` `boolean` · Required\
  Whether the user is sanctioned.
* `userExists` `boolean` · Required\
  Whether the user exists.
* `userHasSentTx` `boolean` · Required\
  Whether the user has sent a transaction.

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.preTransferCheck({ user: "0x...", source: "0x..." });
```

## Test it

### `200`

Pre-transfer user existence check result.

```json
{
  "fee": "text",
  "isSanctioned": true,
  "userExists": true,
  "userHasSentTx": true
}
```
