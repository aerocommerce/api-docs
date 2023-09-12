# View Order

## Attributes

| Name                | Type   | Description                                                                                    |
|---------------------|--------|------------------------------------------------------------------------------------------------|
| `reference`         | string | The **unique** reference for the order                                                         |
| `status`            | object | The status of the order, see [View Order Status](../OrderStatus/VIEW.md)                       |
| `state`             | string | Alternative to passing `status_id`, resolves <br/>the first status with the specified state    |
| `customer`          | object | The customer of the order, see [View Customer](../OrderItem/VIEW.md)                           |
| `email`             | string | The email of the customer that placed the order                                                |
| `subtotal.amount`   | float  | The subtotal of the order **excluding tax**                                                    |
| `subtotal.tax`      | float  | The subtotal tax for the order                                                                 |
| `shipping.amount`   | float  | The shipping of the order **excluding tax**                                                    |
| `shipping.tax`      | float  | The shipping tax for the order                                                                 |
| `discount.amount`   | float  | The discount of the order **excluding tax**                                                    |
| `discount.tax`      | float  | The discount tax for the order                                                                 |
| `surcharge.amount`  | float  | The surcharge of the order **excluding tax**                                                   |
| `surcharge.tax`     | float  | The surcharge tax for the order                                                                |
| `currency`          | string | The currency code of the order                                                                 |
| `shipping_method`   | object | The shipping method of the order, see <br/>[View Shipping Method](../OrderItem/VIEW.md)        |
| `shipping_address`  | object | The shipping address of the order,<br/>see [View Shipping Address](../ShippingAddress/VIEW.md) |
| `billing_address `  | object | The billing address of the order,<br/>see [View Billing Address](../BillingAddress/VIEW.md)    |
| `ordered_at`        | date   | When the order was ordered                                                                     |
| `deliver_on`        | date   | When the order should be delivered                                                             |
| `items`             | array  | The items of the order,<br/>see [View Order Item](../OrderItem/VIEW.md)                        |

## Example Response

```http request
GET /api/orders/{id}
```

```json
{
    "reference": "LTS123456",
    "email": "testing@gmail.com",
    "subtotal": {
        "amount": 84166.67,
        "tax": 16833.33
    },
    "shipping": {
        "amount": 83.33,
        "tax": 16.67
    },
    "discount": {
        "amount": 8416.67,
        "tax": 1683.33
    },
    "surcharge": {
        "amount": 0,
        "tax": 0
    },
    "ordered_at": "2023-09-01T09:29:41.000000Z",
    "deliver_on": null,
    "currency": {
        "code": "GBP",
        "symbol": "£"
    },
    "status": {
        "id": 3,
        "name": "Successful",
        "state": "successful"
    },
    "customer": {
        "id": 1,
        "name": "1",
        "email": "1@gmail.com"
    },
    "shipping_method": {
        "id": 1,
        "name": "Standard"
    },
    "billing_address": {
        "id": 331,
        "first_name": "Aero",
        "last_name": "Commerce",
        "company": "Aero Commerce",
        "mobile": null,
        "phone": null,
        "line_1": "28-32 Albert Rd",
        "line_2": null,
        "city": "Middlesbrough",
        "zone": null,
        "postcode": "TS1 1QD",
        "reference": null,
        "country": "GB",
        "eori_number": null
    },
    "shipping_address": {
        "id": 331,
        "first_name": "Aero",
        "last_name": "Commerce",
        "company": "Aero Commerce",
        "mobile": null,
        "phone": null,
        "line_1": "28-32 Albert Rd",
        "line_2": null,
        "city": "Middlesbrough",
        "zone": null,
        "postcode": "TS1 1QD",
        "reference": null,
        "country": "GB",
        "eori_number": null
    },
    "items": [
        {
            "id": 148,
            "name": "Sandro Paris Checked Trench Coat",
            "sku": "SHPMA00148-M",
            "product_id": 4,
            "variant_id": 14,
            "shippable": true,
            "quantity": 2,
            "price": {
                "amount": 42083.33,
                "tax": 8416.67
            },
            "discount": {
                "amount": 8416.67,
                "tax": 1683.33
            },
            "full_price": {
                "amount": 42083.33,
                "tax": 8416.67
            },
            "weight": 0,
            "volume": 0
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
