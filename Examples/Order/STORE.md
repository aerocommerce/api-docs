# Store Order

## Attributes

| Name                 | Type      | Description                                                                                      | Required?                   |
|----------------------|-----------|--------------------------------------------------------------------------------------------------|-----------------------------|
| `reference`          | string    | The **unique** reference for the order                                                           | No                          |
| `status_id`          | int       | The status id of the order,  can be resolved from <br/>`state` (see below)                       | If `ordered_at` is not null |
| `state`              | string    | Alternative to passing `status_id`, resolves <br/>the first status with the specified state      | No                          |
| `customer_id`        | int       | The id of the customer that placed the order                                                     | No                          |
| `email`              | string    | The email of the customer that placed the order                                                  | No                          |
| `subtotal.amount`    | float     | The subtotal of the order **excluding tax**                                                      | Yes                         |
| `subtotal.tax`       | float     | The subtotal tax for the order                                                                   | Yes                         |
| `shipping.amount`    | float     | The shipping of the order **excluding tax**                                                      | No                          |
| `shipping.tax`       | float     | The shipping tax for the order                                                                   | No                          |
| `discount.amount`    | float     | The discount of the order **excluding tax**                                                      | No                          |
| `discount.tax`       | float     | The discount tax for the order                                                                   | No                          |
| `surcharge.amount`   | float     | The surcharge of the order **excluding tax**                                                     | No                          |
| `surcharge.tax`      | float     | The surcharge tax for the order                                                                  | No                          |
| `shipping_method_id` | int       | The shipping method id of the order                                                              | No                          |
| `currency`           | string    | The currency of the order, set to store currency<br/>if not supplied                             | No                          |
| `shipping_address`   | object    | The shipping address of the order,<br/>see [Store Shipping Address](../ShippingAddress/STORE.md) | No                          |
| `billing_address `   | object    | The billing address of the order,<br/>see [Store Billing Address](../BillingAddress/STORE.md)    | No                          |
| `ip`                 | string    | The ip of the order                                                                              | No                          |
| `channel`            | string    | The channel of the order                                                                         | No                          |
| `subscription_id`    | int       | The subscription id of the order                                                                 | No                          |
| `notify`             | boolean   | Whether the order notifications are muted                                                        | No                          |
| `ordered_at`         | date      | When the order was ordered                                                                       | No                          |
| `deliver_on`         | date      | When the order should be delivered                                                               | No                          |
| `items`              | array     | The items of the order,<br/>see [Store Order Item](../OrderItem/STORE.md)                        | Yes                         |

## Remarks

If no `"currency"` is passed for the order it is resolved from the store default

If no `"full_price"` is passed for the order item it is set to its `"price"`

If no `"key"`/`"name"`/`"url"`/`"sku"`/`"image"` is passed for the order item they are resolved from its buyable

## Example Request

```http request
POST /api/orders
```

```json lines
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
    "ordered_at": "2023-09-01T09:29:41.000000Z",
    "currency": "GBP", 
    "status_id": 3, 
    "customer_id": 1, 
    "shipping_method_id": 1, 
    "notify": true, 
    "billing_address": { 
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
        }
    ]
}
```

## Example Response

```json
{
    "order": {
        "id": 27
    }
}
```

[Back to contents](../../README.md#table-of-contents)
