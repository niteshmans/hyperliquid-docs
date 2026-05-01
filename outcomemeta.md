# outcomeMeta

Request prediction market outcome metadata.

## Body

`application/json`

| Field  | Type             | Required | Description                                     |
| ------ | ---------------- | -------- | ----------------------------------------------- |
| `type` | undefined · enum | Yes      | Type of request. Possible values: `outcomeMeta` |

## Responses

### `200`

Prediction market outcome metadata including outcomes and questions.

`application/json`

| Field       | Type      | Required | Description                           |
| ----------- | --------- | -------- | ------------------------------------- |
| `outcomes`  | object\[] | Yes      | Array of prediction market outcomes.  |
| `questions` | object\[] | Yes      | Array of prediction market questions. |

### `422`

Failed to deserialize the JSON body into the target type

`text/plain`

### `500`

Internal Server Error

`application/json`

## TypeScript

```typescript
import * as hl from "@devmike/hyperliquid-sdk";

const transport = new hl.HttpTransport(); // or `WebSocketTransport`
const client = new hl.InfoClient({ transport });

const data = await client.outcomeMeta();
```

## Example response

`200`

Prediction market outcome metadata including outcomes and questions.

```json
{
  "outcomes": [
    {
      "outcome": 1,
      "name": "text",
      "description": "text",
      "sideSpecs": [
        {
          "name": "text",
          "token": 1
        }
      ]
    }
  ],
  "questions": [
    {
      "question": 1,
      "name": "text",
      "description": "text",
      "fallbackOutcome": 1,
      "namedOutcomes": [
        1
      ],
      "settledNamedOutcomes": [
        1
      ]
    }
  ]
}
```
