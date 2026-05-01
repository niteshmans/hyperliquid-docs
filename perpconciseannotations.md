# perpConciseAnnotations

**POST** `/info`

## Base URLs

* Mainnet: `https://api.hyperliquid.xyz`
* Testnet: `https://api.hyperliquid-testnet.xyz`

## Request

Request concise annotations for all perpetual assets.

### Body

`application/json`

| Field  | Type                | Required | Description      | Possible values          |
| ------ | ------------------- | -------- | ---------------- | ------------------------ |
| `type` | `undefined \| enum` | Yes      | Type of request. | `perpConciseAnnotations` |

## Responses

### 200

Array of tuples mapping coin names to their concise annotations.

`application/json`

### 422

Failed to deserialize the JSON body into the target type

`text/plain`

### 500

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.perpConciseAnnotations();
```

## Test it

### 200

Array of tuples mapping coin names to their concise annotations.

```json
[
  []
]
```
