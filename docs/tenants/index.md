# Tenants

icruiting is a multi-tenant system, which means there are multiple, independent, logically isolated, conceptual instances of icruiting operating in a single shared environment.

In the context of icruiting, a tenant is a conceptual border that isolates multiple user accounts, forms, jobs and more that all belong together.

Take a look at the following article explaining multiple ways of implementing multi-tenancy in REST: [Multi-tenancy in REST API](https://medium.com/@vivekmadurai/multi-tenancy-in-rest-api-a570d728620c)

_Base URL:_ `/tenants/`

## The tenant object

| Attribute        | Type                | Description                                                                          |
| ---------------- | ------------------- | ------------------------------------------------------------------------------------ |
| id               | `string`            | A unique identifier.                                                                 |
| tenantName       | `string`            | The tenant's name, meant to be displayable to the users.                             |
| stripeCustomerId | `string` (optional) | The id of the connected [Stripe customer](https://stripe.com/docs/api/customers).    |
| createdAt        | `timestamp`         | Time at which the object was created. Measured in seconds since the Unix epoch.      |
| updatedAt        | `timestamp`         | Time at which the object was last updated. Measured in seconds since the Unix epoch. |

```json
{
  "id": "751a9125-2a9e-4326-8c04-2a659d2a1af7",
  "tenantName": "Quokka GmbH",
  "stripeCustomerId": "cus_4QE4N83DfMpDkX",
  "createdAt": "1650100049",
  "updatedAt": "1650109049"
}
```

## Create a tenant

Creating a tenant combines two actions: Creating a tenant object and registering an administrator as its first user.
Besides creating a simple tenant entity in the database, this also includes creating a stripe customer and a new subscription using the provided price id. The subscription will start with a 14 days Trial period without a payment method required.

_Request:_ `POST /tenants/`

| Parameter     | Type     | Description                                                                                                                                                                                         |
| ------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| tenantName    | `string` | The tenant's name, meant to be displayable to the users.                                                                                                                                            |
| email         | `string` | The email of the user to register.                                                                                                                                                                  |
| password      | `string` | The password of the user to register.                                                                                                                                                               |
| stripePriceId | `string` | The id of the selected [Stripe price](https://stripe.com/docs/api/prices/object?lang=curl#price_object-id). It is used to create a [Stipe subscription](https://stripe.com/docs/api/subscriptions). |

```bash
curl -X POST http://localhost:5000/tenants \
   -H 'Content-Type: application/json' \
   -d '{"tenantName":"Quokka GmbH","email":"contact@quokkagmbh.com","password":"Pa$$w0rd","stripePriceId":"price_1Hn2G4LVXwV99McgqNOmeDA8"}'
```

_Response:_ A [tenant object](#the-tenant-object).

## Delete a tenant

Delete a tenant and all it's related entities (jobs, forms, users, applicants, ...) including the connected Stripe Customer.

_Request:_ `DELETE /tenants/:id/`

```bash
curl -X DELETE http://localhost:5000/tenants/a1352c18-d64d-44f2-8b39-5c27b4d298c7 \
    -H 'Authorization: Bearer {IdToken}'
```

_Response:_ `{}`
