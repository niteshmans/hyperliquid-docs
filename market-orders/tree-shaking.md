# Tree-shaking

The SDK is organized into modular entry points so bundlers can eliminate unused code.

### Entry points

The following table lists the available entry points:

| Entry point                            | Contains                                       |
| -------------------------------------- | ---------------------------------------------- |
| `@devmike/hyperliquid-sdk`                  | Transports, clients, error classes             |
| `@devmike/hyperliquid-sdk/signing`          | Signing functions, wallet utilities            |
| `@devmike/hyperliquid-sdk/utils`            | `formatPrice`, `formatSize`, `SymbolConverter` |
| `@devmike/hyperliquid-sdk/api/info`         | Info methods, individually importable          |
| `@devmike/hyperliquid-sdk/api/exchange`     | Exchange methods, individually importable      |
| `@devmike/hyperliquid-sdk/api/subscription` | Subscription methods, individually importable  |

Each entry point has independent dependencies. Importing `@devmike/hyperliquid-sdk/utils` doesn't pull in signing or validation code.

### Direct method imports

Instead of creating a [client](../clients.md) (which bundles all methods), import individual methods directly. Each method accepts the same config as its client as the first argument.

Info methods use [`InfoClient`](../clients.md#read-data) config:

```ts
import { HttpTransport } from "@devmike/hyperliquid-sdk";
import { allMids } from "@devmike/hyperliquid-sdk/api/info";

const transport = new HttpTransport();
const result = await allMids({ transport });
```

This bundles only the `allMids` method, its validation schema, and the transport logic — not the full `InfoClient` with all methods.

Exchange methods use [`ExchangeClient`](../clients.md#trading) config:

```ts
import { HttpTransport } from "@devmike/hyperliquid-sdk";
import { order } from "@devmike/hyperliquid-sdk/api/exchange";
import { privateKeyToAccount } from "viem/accounts";

const transport = new HttpTransport();
const wallet = privateKeyToAccount("0x...");

await order(
  { transport, wallet },
  {
    orders: [{
      a: 0,
      b: true,
      p: "50000",
      s: "0.01",
      r: false,
      t: { limit: { tif: "Gtc" } },
    }],
    grouping: "na",
  },
);
```

Subscription methods use [`SubscriptionClient`](../clients.md#real-time-updates) config:

```ts
import { WebSocketTransport } from "@devmike/hyperliquid-sdk";
import { allMids } from "@devmike/hyperliquid-sdk/api/subscription";

const transport = new WebSocketTransport();
const subscription = await allMids({ transport }, (data) => {
  console.log(data.mids);
});
```
