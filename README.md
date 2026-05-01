# Introduction

A community-supported [Hyperliquid API](https://hyperliquid.gitbook.io/hyperliquid-docs/for-developers/api) SDK for all major JS runtimes, written in TypeScript.

### Installation

{% tabs %}
{% tab title="npm" %}
```bash
npm i @devmike/hyperliquid-sdk
```
{% endtab %}

{% tab title="pnpm" %}
```bash
pnpm add @devmike/hyperliquid-sdk
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add @devmike/hyperliquid-sdk
```
{% endtab %}

{% tab title="bun" %}
```bash
bun add @devmike/hyperliquid-sdk
```
{% endtab %}

{% tab title="deno" %}
```bash
deno add jsr:@devmike/hyperliquid-sdk
```
{% endtab %}

{% tab title="CDN" %}
```html
<script type="module">
  import * as hl from "https://esm.sh/jsr/@devmike/hyperliquid-sdk";
</script>
```
{% endtab %}
{% endtabs %}

### Quick start

{% tabs %}
{% tab title="InfoClient" %}
Read market data, account state, order book. [Learn more](clients.md#read-data)

```typescript
import { HttpTransport, InfoClient } from "@devmike/hyperliquid-sdk";

const transport = new HttpTransport();
const client = new InfoClient({ transport });

const mids = await client.allMids();
```
{% endtab %}

{% tab title="ExchangeClient" %}
Place orders, transfer funds, manage accounts. [Learn more](clients.md#trading)

```typescript
import { ExchangeClient, HttpTransport } from "@devmike/hyperliquid-sdk";
import { privateKeyToAccount } from "viem/accounts";

const wallet = privateKeyToAccount("0x...");

const transport = new HttpTransport();
const client = new ExchangeClient({ transport, wallet });

await client.order({
  orders: [{
    a: 0,
    b: true,
    p: "50000",
    s: "0.01",
    r: false,
    t: { limit: { tif: "Gtc" } },
  }],
  grouping: "na",
});
```
{% endtab %}

{% tab title="SubscriptionClient" %}
Receive real-time updates via WebSocket. [Learn more](clients.md#real-time-updates)

```typescript
import { SubscriptionClient, WebSocketTransport } from "@devmike/hyperliquid-sdk";

const transport = new WebSocketTransport();
const client = new SubscriptionClient({ transport });

await client.allMids((data) => {
  console.log(data.mids);
});
```
{% endtab %}
{% endtabs %}
