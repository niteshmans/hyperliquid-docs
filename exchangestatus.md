# exchangeStatus

Request exchange system status information.

## Body

`application/json`

* `type` — `undefined · enum` (Required)
  * Type of request.
  * Possible values: `exchangeStatus`

## Responses

### 200

Exchange system status information.

`application/json`

* `time` — `number` (Required)
  * Server time (in ms since epoch).
* `specialStatuses` — `any of` (nullable, optional)
  * Special statuses of the exchange system.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.exchangeStatus();
```

## Test it

### 200

Exchange system status information.

```json
{
  "time": 1,
  "specialStatuses": null
}
```
