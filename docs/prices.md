# Prices

See [Stripes documentation](https://stripe.com/docs/api/prices) about prices for more info.

_Request:_ `GET /products/`

```bash
curl -X GET http://localhost:5000/prices
```

_Response:_ A list of [Stripe prices](https://stripe.com/docs/api/prices/object) with the [products](https://stripe.com/docs/api/products/object) property expanded.
