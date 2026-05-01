# referral

`POST /info`

Mainnet: `https://api.hyperliquid.xyz`\
Testnet: `https://api.hyperliquid-testnet.xyz`

## Body

`application/json`

* `type` — undefined · enum · Required\
  Type of request. Possible values: `referral`
* `user` — string · min: 42 · max: 42 · Required\
  User address.\
  Pattern: `^0[xX][0-9a-fA-F]+$`

## Responses

### 200

Referral details for a user.

`application/json`

* `referredBy` — any of · Required\
  Referrer details.
* `cumVlm` — string · Required\
  Cumulative traded volume.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `unclaimedRewards` — string · Required\
  Rewards earned but not yet claimed.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `claimedRewards` — string · Required\
  Rewards that have been claimed.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `builderRewards` — string · Required\
  Builder reward amount.\
  Pattern: `^[0-9]+(\.[0-9]+)?$`
* `referrerState` — any of · Required\
  Current state of the referrer.
* `rewardHistory` — object\[] · Required\
  History of referral rewards.
* `tokenToState` — any\[]\[] · Required\
  Mapping of token IDs to referral reward states.

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

const data = await client.referral({ user: "0x..." });
```

## Test it

### 200

Referral details for a user.

```json
{
  "referredBy": {
    "referrer": "text",
    "code": "text"
  },
  "cumVlm": "text",
  "unclaimedRewards": "text",
  "claimedRewards": "text",
  "builderRewards": "text",
  "referrerState": {
    "stage": "ready",
    "data": {
      "code": "text",
      "nReferrals": 1,
      "referralStates": [
        {
          "cumVlm": "text",
          "cumRewardedFeesSinceReferred": "text",
          "cumFeesRewardedToReferrer": "text",
          "timeJoined": 1,
          "user": "text",
          "tokenToState": [
            []
          ]
        }
      ]
    }
  },
  "rewardHistory": [
    {
      "earned": "text",
      "vlm": "text",
      "referralVlm": "text",
      "time": 1
    }
  ],
  "tokenToState": [
    []
  ]
}
```
