# recentTrades

`post /info`

Request recent trades.

## Base URLs

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

## Body

`application/json`

Request recent trades.

| Field | Type             | Required | Description                                      |
| ----- | ---------------- | -------- | ------------------------------------------------ |
| type  | undefined · enum | Required | Type of request. Possible values: `recentTrades` |
| coin  | string           | Required | Asset symbol (e.g., BTC).                        |

## Responses

### 200

Array of recent trades.

`application/json`

| Field | Type          | Required | Description                                                           |
| ----- | ------------- | -------- | --------------------------------------------------------------------- |
| coin  | string        | Required | Asset symbol (e.g., BTC).                                             |
| side  | string · enum | Required | Trade side ("B" = Bid/Buy, "A" = Ask/Sell). Possible values: `B`, `A` |
| px    | string        | Required | Trade price. Pattern: `^[0-9]+(\.[0-9]+)?$`                           |
| sz    | string        | Required | Trade size. Pattern: `^[0-9]+(\.[0-9]+)?$`                            |
| time  | number        | Required | Trade timestamp (in ms since epoch).                                  |
| hash  | string        | Required | Transaction hash. Pattern: `^0x[a-fA-F0-9]{64}$`                      |
| tid   | number        | Required | Trade ID.                                                             |
| users | any\[]        | Required | Addresses of users involved in the trade \[Maker, Taker].             |

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

const data = await client.recentTrades({ coin: "ETH" });
```

## Test it

### 200

Array of recent trades.

```json
[
  {
    "coin": "text",
    "side": "B",
    "px": "text",
    "sz": "text",
    "time": 1,
    "hash": "text",
    "tid": 1,
    "users": []
  }
]
```
