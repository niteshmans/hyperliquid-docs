# spotPairDeployAuctionStatus

## Body

**application/json**

Request for the status of the spot deploy auction.

*   `type` — `undefined` · enum · Required

    Type of request.

    Possible values: `spotPairDeployAuctionStatus`

## Responses

### 200

Status of the spot deploy auction.

**application/json**

`any` Optional

Status of the spot deploy auction.

### 422

Failed to deserialize the JSON body into the target type

**text/plain**

### 500

Internal Server Error

**application/json**

## TypeScript

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.spotPairDeployAuctionStatus();
```
