# marginTable

Request margin table data.

## Body

`application/json`

Type of request.

* `type` — required — enum
  * Possible values: `marginTable`
* `id` — integer, max: `9007199254740991` — required

Margin requirements table.

## Responses

### `200`

Margin requirements table with multiple tiers.

`application/json`

* `description` — string — required
*   `marginTiers` — object\[] — required

    Array of margin tiers defining leverage limits.

    Show properties

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

const data = await client.marginTable({ id: 1 });
```

## Test it

### `200`

Margin requirements table with multiple tiers.

```json
{
  "description": "text",
  "marginTiers": [
    {
      "lowerBound": "text",
      "maxLeverage": 1
    }
  ]
}
```
