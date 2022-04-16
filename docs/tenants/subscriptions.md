# Subscriptions

## List Subscriptions

List the currently active subscriptions.

_Request:_ `GET /subscriptions`

```bash
curl http://localhost:5000/subscriptions -H 'Authorization: Bearer {IdToken}' \
```

_Response:_ A list of [Stripe subscriptions](https://stripe.com/docs/api/subscriptions/object).

## Update Subscription

Update the currently active subscriptions.

_Request:_ `PUT /subsctipsions/:id`

| Properties    | Type     | Description          |
| ------------- | -------- | -------------------- |
| stripePriceId | `string` | A unique identifier. |

```bash
curl -X PUT http://localhost:5000/subscriptions/sub_1KpFJ6LVXwV99Mcgj6SMLOIX \
   -H 'Authorization: Bearer {IdToken}' \
   -H 'Content-Type: application/json' \
   -d '{"stripePriceId":"price_1Hn2G4LVXwV99McgqNOmeDA8"}'
```
