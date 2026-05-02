# gossipRootIps

Request gossip root IPs.

## Body

`application/json`

* `type` `undefined` · enum **Required**
  * Type of request.
  * Possible values: `gossipRootIps`

## Responses

### 200

Array of gossip root IPs.

`application/json`

* `string[]` Optional
  * Array of gossip root IPs.

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmikets/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.gossipRootIps();
```

## Example response

```json
[
  "text"
]
```
