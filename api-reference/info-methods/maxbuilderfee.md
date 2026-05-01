# maxBuilderFee

Request builder fee approval.

## Body

`application/json`

| Field     | Type   | Required | Description                                       | Constraints                    |
| --------- | ------ | -------- | ------------------------------------------------- | ------------------------------ |
| `type`    | enum   | Yes      | Type of request. Possible values: `maxBuilderFee` |                                |
| `user`    | string | Yes      | User address.                                     | Pattern: `^0[xX][0-9a-fA-F]+$` |
| `builder` | string | Yes      | Builder address.                                  | Pattern: `^0[xX][0-9a-fA-F]+$` |

## Responses

| Status | Description                                              | Content type       | Schema   |
| ------ | -------------------------------------------------------- | ------------------ | -------- |
| `200`  | Maximum builder fee approval.                            | `application/json` | `number` |
| `422`  | Failed to deserialize the JSON body into the target type | `text/plain`       |          |
| `500`  | Internal Server Error                                    | `application/json` |          |

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.maxBuilderFee({ user: "0x...", builder: "0x..." });
```

## Example response

`200` — Maximum builder fee approval.

```
1
```
