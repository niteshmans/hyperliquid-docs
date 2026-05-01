# allMids

Request mid coin prices.

## Body

`application/json`

### Fields

* `type` **required** — Type of request.
  * Possible values: `allMids`
* `dex` **optional** — DEX name (empty string for main dex).

## Responses

### `200`

Mapping of coin symbols to mid prices.

`application/json`

* Other properties: `string` — Optional
* Pattern: `^[0-9]+(\.[0-9]+)?$`

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.allMids();
```

## Example response

```json
{
  "ANY_ADDITIONAL_PROPERTY": "text"
}
```
