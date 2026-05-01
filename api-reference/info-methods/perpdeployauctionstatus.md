# perpDeployAuctionStatus

### POST `/info`

{% tabs %}
{% tab title="Mainnet" %}
https://api.hyperliquid.xyz
{% endtab %}

{% tab title="Testnet" %}
https://api.hyperliquid-testnet.xyz
{% endtab %}
{% endtabs %}

Request for the status of the perpetual deploy auction.

#### Body

`application/json`

Request for the status of the perpetual deploy auction.

*   `type` `undefined · enum` **Required**\
    Type of request.

    Possible values: `perpDeployAuctionStatus`

#### Responses

**`200`**

Status of the perpetual deploy auction.

`application/json`

Status of the perpetual deploy auction.

*   `currentGas` `string · nullable` **Required**\
    Current gas.

    Pattern: `^[0-9]+(\.[0-9]+)?$`
* `durationSeconds` `number` **Required**\
  Duration in seconds.
*   `endGas` `string · nullable` **Required**\
    Ending gas.

    Pattern: `^[0-9]+(\.[0-9]+)?$`
*   `startGas` `string` **Required**\
    Starting gas.

    Pattern: `^[0-9]+(\.[0-9]+)?$`
* `startTimeSeconds` `number` **Required**\
  Auction start time (seconds since epoch).

**`422`**

Failed to deserialize the JSON body into the target type

`text/plain`

**`500`**

Internal Server Error

`application/json`

### TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.perpDeployAuctionStatus();
```

### Test it

#### `200`

Status of the perpetual deploy auction.

```json
{
  "currentGas": "text",
  "durationSeconds": 1,
  "endGas": "text",
  "startGas": "text",
  "startTimeSeconds": 1
}
```
