# userFees

Request user fees.

## Body

`application/json`

| Field  | Type                | Required | Description                                  |
| ------ | ------------------- | -------- | -------------------------------------------- |
| `type` | `undefined` \| enum | Yes      | Type of request. Possible value: `userFees`  |
| `user` | `string`            | Yes      | User address. Pattern: `^0[xX][0-9a-fA-F]+$` |

## Responses

### `200`

User fees.

| Field                         | Type       | Required | Description                                                                                                                                                                            |
| ----------------------------- | ---------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `dailyUserVlm`                | `object[]` | Yes      | Daily user volume metrics.                                                                                                                                                             |
| `feeSchedule`                 | `object`   | Yes      | Fee schedule information.                                                                                                                                                              |
| `userCrossRate`               | `string`   | Yes      | User cross-trade rate. Pattern: `^[0-9]+(\.[0-9]+)?$`                                                                                                                                  |
| `userAddRate`                 | `string`   | Yes      | User add-liquidity rate. Pattern: `^[0-9]+(\.[0-9]+)?$`                                                                                                                                |
| `userSpotCrossRate`           | `string`   | Yes      | User spot cross-trade rate. Pattern: `^[0-9]+(\.[0-9]+)?$`                                                                                                                             |
| `userSpotAddRate`             | `string`   | Yes      | User spot add-liquidity rate. Pattern: `^[0-9]+(\.[0-9]+)?$`                                                                                                                           |
| `activeReferralDiscount`      | `string`   | Yes      | Active referral discount rate. Pattern: `^[0-9]+(\.[0-9]+)?$`                                                                                                                          |
| `trial`                       | `any of`   | Yes      | Trial details. `any` · nullable · Optional                                                                                                                                             |
| `feeTrialEscrow`              | `string`   | Yes      | Fee trial escrow amount. Pattern: `^[0-9]+(\.[0-9]+)?$`                                                                                                                                |
| `nextTrialAvailableTimestamp` | `any of`   | Yes      | Timestamp when next trial becomes available. `any` · nullable · Optional                                                                                                               |
| `stakingLink`                 | `object`   | Yes      | Permanent link between staking and trading accounts. Staking user gains full control of trading account funds. Staking user forfeits own fee discounts. `object` · nullable · Optional |
| `activeStakingDiscount`       | `object`   | Yes      | Active staking discount details.                                                                                                                                                       |

#### `feeSchedule`

* `cross`
* `add`
* `spotCross`
* `spotAdd`
* `tiers`
  * `vip`
    * `ntlCutoff`
    * `cross`
    * `add`
    * `spotCross`
    * `spotAdd`
  * `mm`
    * `makerFractionCutoff`
    * `add`
* `referralDiscount`
* `stakingDiscountTiers`
  * `bpsOfMaxSupply`
  * `discount`

#### `dailyUserVlm`

* `date`
* `userCross`
* `userAdd`
* `exchange`

#### `stakingLink`

* `stakingUser`
* `type`: `requested`

#### `activeStakingDiscount`

* `bpsOfMaxSupply`
* `discount`

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```ts
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.userFees({ user: "0x..." });
```

## Test it

### `200`

User fees.

```json
{
  "dailyUserVlm": [
    {
      "date": "text",
      "userCross": "text",
      "userAdd": "text",
      "exchange": "text"
    }
  ],
  "feeSchedule": {
    "cross": "text",
    "add": "text",
    "spotCross": "text",
    "spotAdd": "text",
    "tiers": {
      "vip": [
        {
          "ntlCutoff": "text",
          "cross": "text",
          "add": "text",
          "spotCross": "text",
          "spotAdd": "text"
        }
      ],
      "mm": [
        {
          "makerFractionCutoff": "text",
          "add": "text"
        }
      ]
    },
    "referralDiscount": "text",
    "stakingDiscountTiers": [
      {
        "bpsOfMaxSupply": "text",
        "discount": "text"
      }
    ]
  },
  "userCrossRate": "text",
  "userAddRate": "text",
  "userSpotCrossRate": "text",
  "userSpotAddRate": "text",
  "activeReferralDiscount": "text",
  "trial": null,
  "feeTrialEscrow": "text",
  "nextTrialAvailableTimestamp": null,
  "stakingLink": {
    "stakingUser": "text",
    "type": "requested"
  },
  "activeStakingDiscount": {
    "bpsOfMaxSupply": "text",
    "discount": "text"
  }
}
```
