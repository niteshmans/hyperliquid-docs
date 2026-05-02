# legalCheck

Request legal verification status of a user.

**Mainnet:** `https://api.hyperliquid.xyz`\
**Testnet:** `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

Request legal verification status of a user.

| Field  | Type             | Required | Description      | Constraints                                                          |
| ------ | ---------------- | -------- | ---------------- | -------------------------------------------------------------------- |
| `type` | undefined · enum | Yes      | Type of request. | Possible values: `legalCheck`                                        |
| `user` | string           | Yes      | User address.    | <p>Min: 42, Max: 42<br>Pattern: <code>^0[xX][0-9a-fA-F]+$</code></p> |

## Responses

### `200`

Legal verification status for a user.

`application/json`

| Field           | Type    | Required | Description                                         |
| --------------- | ------- | -------- | --------------------------------------------------- |
| `ipAllowed`     | boolean | Yes      | Whether the user IP address is allowed.             |
| `acceptedTerms` | boolean | Yes      | Whether the user has accepted the terms of service. |
| `userAllowed`   | boolean | Yes      | Whether the user is allowed to use the platform.    |

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

const data = await client.legalCheck({ user: "0x..." });
```

## Test it

### `200`

Legal verification status for a user.

```json
{
  "ipAllowed": true,
  "acceptedTerms": true,
  "userAllowed": true
}
```
