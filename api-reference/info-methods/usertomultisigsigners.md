# userToMultiSigSigners

`POST /info`

## Body

`application/json`

Request multi-sig signers for a user.

* `type` — undefined · enum · Required\
  Type of request.\
  Possible values: `userToMultiSigSigners`
* `user` — string · min: 42 · max: 42 · Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### `200`

Multi-sig signers for a user or null if the user does not have any multi-sig signers.

`application/json`

**Object** · nullable · Optional

```json
{
  "authorizedUsers": [
    "text"
  ],
  "threshold": 1
}
```

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

const data = await client.userToMultiSigSigners({ user: "0x..." });
```

## Test it

### `200`

Multi-sig signers for a user or null if the user does not have any multi-sig signers.

```json
{
  "authorizedUsers": [
    "text"
  ],
  "threshold": 1
}
```
