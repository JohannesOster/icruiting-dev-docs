# Payment Methods

Payment Methods are a direct wrapper around Stripes [Payment Method](https://stripe.com/docs/api/payment_methods) and [Setup Intent](https://stripe.com/docs/api/setup_intents) functionality.
See the above documentation to learn more about the underlying Stripe payment process.

## Create Setup Intent

_Request:_ `POST /setup-intents/`

```bash
curl -X POST http://localhost:5000/setup-intents \
    -H 'Authorization: Bearer {IdToken}'
```

_Response:_ The client secret (`string`) of the setup intent.

## List Payment Methods

List of payment methods currently set up in the tenant.

_Request:_ `GET /payment-methods/`

```bash
curl -X POST http://localhost:5000/payment-methods \
    -H 'Authorization: Bearer {IdToken}'
```

_Response:_ See [Stripe List Payment Methods](https://stripe.com/docs/api/payment_methods/list)

## Delete Payment Method

Delete payment method.

_Request:_ `DELETE /payment-methods/:id`

```bash
curl -X DELETE http://localhost:5000/payment-methods/:id \
    -H "Authorization: Bearer {IdToken}"
```

_Response:_ `{}`

## Set Default Payment Method

List of payment method.

_Request:_ `PUT /payment-methods/default`

| Parameter       | Type     | Description          |
| --------------- | -------- | -------------------- |
| paymentMethodId | `string` | A unique identifier. |

```json
{
  "paymentMethodId": "pm_1KoElj2eZvKYlo2CBcT7cvQ1"
}
```

```bash
curl -X PUT http://localhost:5000/payment-methods/default \
    -H 'Authorization: Bearer {IdToken}' \
    -d '{"paymentMethodId": "pm_1KoElj2eZvKYlo2CBcT7cvQ1"}'
```

_Response:_ `{}`
