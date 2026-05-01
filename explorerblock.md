# explorerBlock

`post`

**WebSocket endpoints**

* `wss://api.hyperliquid.xyz/ws`
* `wss://api.hyperliquid-testnet.xyz/ws`

Subscription to explorer block events.

## Body

`application/json`

| Field  | Type | Required | Description           | Possible values |
| ------ | ---- | -------- | --------------------- | --------------- |
| `type` | enum | Yes      | Type of subscription. | `explorerBlock` |

## Responses

### 200

Event of array of block details.

| Field       | Type   | Required | Description                                            |
| ----------- | ------ | -------- | ------------------------------------------------------ |
| `blockTime` | number | Yes      | Block creation timestamp.                              |
| `hash`      | string | Yes      | Block hash. Pattern: `^0x[a-fA-F0-9]{64}$`             |
| `height`    | number | Yes      | Block height in chain.                                 |
| `numTxs`    | number | Yes      | Total transactions in block.                           |
| `proposer`  | string | Yes      | Block proposer address. Pattern: `^0x[a-fA-F0-9]{40}$` |

## Example

```typescript
import * as hl from "@nktkas/hyperliquid";

const transport = new hl.WebSocketTransport({ url: "wss://rpc.hyperliquid.xyz/ws" }); // RPC endpoint
const client = new hl.SubscriptionClient({ transport });

const sub = await client.explorerBlock((data) => {
  console.log(data);
});
```

### 200

Event of array of block details.

```json
[
  {
    "blockTime": 1,
    "hash": "text",
    "height": 1,
    "numTxs": 1,
    "proposer": "text"
  }
]
```
