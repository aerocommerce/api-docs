# Store Order

## Attributes:

### Order

| Name                 | Type      | Description                                                                                             | Required?                   |
|----------------------|-----------|---------------------------------------------------------------------------------------------------------|-----------------------------|
| `reference`          | string    | The **unique** reference for the order                                                                  | No                          |
| `status_id`          | int       | The status id of the order,  can be resolved from <br/>`state` (see below)                              | If `ordered_at` is not null |
| `state`              | string    | Alternative to passing `status_id`, resolves <br/>the first status with the specified state             | No                          |
| `customer_id`        | int       | The id of the customer that placed the order                                                            | No                          |
| `email`              | string    | The email of the customer that placed the order                                                         | No                          |
| `subtotal.amount`    | float     | The subtotal of the order **excluding tax**                                                             | No                          |
| `subtotal.tax`       | float     | The subtotal tax for the order                                                                          | No                          |
| `shipping.amount`    | float     | The shipping of the order **excluding tax**                                                             | No                          |
| `shipping.tax`       | float     | The shipping tax for the order                                                                          | No                          |
| `discount.amount`    | float     | The discount of the order **excluding tax**                                                             | No                          |
| `discount.tax`       | float     | The discount tax for the order                                                                          | No                          |
| `surcharge.amount`   | float     | The surcharge of the order **excluding tax**                                                            | No                          |
| `surcharge.tax`      | float     | The surcharge tax for the order                                                                         | No                          |
| `shipping_method_id` | int       | The shipping method id of the order                                                                     | No                          |
| `currency`           | string    | The currency of the order, set to store currency<br/>if not supplied                                    | No                          |
| `shipping_address`   | object    | The shipping address of the order,<br/>see [Shipping Address](#shipping-address)                        | No                          |
| `billing_address `   | object    | The billing address of the order,<br/>see [Billing Address](#billing-address)                           | No                          |
| `ip`                 | string    | The ip of the order                                                                                     | No                          |
| `channel`            | string    | The channel of the order                                                                                | No                          |
| `subscription_id`    | int       | The subscription id of the order                                                                        | No                          |
| `notify`             | boolean   | Whether the order notifications are activated                                                           | No                          |
| `buy_items`          | boolean   | Whether the order items stock should be mutated. If false then `OrderItemBought` event will not be emit | No, defaults to `true`      |
| `ordered_at`         | date      | When the order was ordered                                                                              | No                          |
| `deliver_on`         | date      | When the order should be delivered                                                                      | No                          |
| `items`              | array     | The items of the order,<br/>see [Order Item](#order-items)                                              | Yes                         |

If no `subtotal.amount` or `subtotal.tax` is passed their values will be set to the sum of the items `price.amount` * `quantity` & `price.tax` * `quantity` respectively

If no `discount.amount` or `discount.tax` is passed their values will be set to the sum of the items `discount.amount` & `discount.tax` respectively

If no `currency` is passed for the order it is resolved from the store default

### Shipping Address

You can optionally provide a shipping address for the order using these attributes

| Name                               | Type    | Description                                       | Required? |
|------------------------------------|---------|---------------------------------------------------|-----------|
| `shipping_address.first_name`      | string  | The first name for the shipping address           | Yes       |
| `shipping_address.last_name`       | string  | The last name for the shipping address            | Yes       |
| `shipping_address.company`         | string  | The company for the shipping address              | No        |
| `shipping_address.mobile`          | string  | The mobile number for the shipping address        | No        |
| `shipping_address.phone`           | string  | The phone number for the shipping address         | No        |
| `shipping_address.line_1`          | string  | The first line for the shipping address           | Yes       |
| `shipping_address.line_2`          | string  | The second line for the shipping address          | No        |
| `shipping_address.city`            | string  | The city for the shipping address                 | Yes       |
| `shipping_address.zone`            | string  | The zone code for the shipping address            | No        |
| `shipping_address.postcode`        | string  | The postcode for the shipping address             | No        |
| `shipping_address.country`         | string  | The country code for the shipping address         | No        |
| `shipping_address.reference`       | string  | The **unique** reference for the shipping address | No        |
| `shipping_address.eori_number`     | string  | The EORI number for the shipping address          | No        |

### Billing Address

You can optionally provide a billing address for the order using these attributes

| Name                            | Type    | Description                                      | Required? |
|---------------------------------|---------|--------------------------------------------------|-----------|
| `billing_address.first_name`    | string  | The first name for the billing address           | Yes       |
| `billing_address.last_name`     | string  | The last name for the billing address            | Yes       |
| `billing_address.company`       | string  | The company for the billing address              | No        |
| `billing_address.mobile`        | string  | The mobile number for the billing address        | No        |
| `billing_address.phone`         | string  | The phone number for the billing address         | No        |
| `billing_address.line_1`        | string  | The first line for the billing address           | Yes       |
| `billing_address.line_2`        | string  | The second line for the billing address          | No        |
| `billing_address.city`          | string  | The city for the billing address                 | Yes       |
| `billing_address.zone`          | string  | The zone code for the billing address            | No        |
| `billing_address.postcode`      | string  | The postcode for the billing address             | No        |
| `billing_address.country`       | string  | The country code for the billing address         | No        |
| `billing_address.reference`     | string  | The **unique** reference for the billing address | No        |
| `billing_address.eori_number`   | string  | The EORI number for the billing address          | No        |

### Order Items

You must provide an array of items for the order using these attributes

| Name                           | Type    | Description                                                                                       | Required?                                                                |
|--------------------------------|---------|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| `items.*.key`                  | string  | The key for the order item                                                                        | No                                                                       |
| `items.*.variant_id`           | int     | The variant id of the buyable                                                                     | No                                                                       |
| `items.*.product_id`           | string  | The product id of the buyable (resolves first variant)                                            | No                                                                       |
| `items.*.buyable_type`         | string  | The buyable type of the order item                                                                | Not required if any of:<br/>`sku`/`variant_id`/`product_id` are provided |
| `items.*.buyable_id`           | int     | The buyable id of the order item                                                                  | Not required if any of:<br/>`sku`/`variant_id`/`product_id` are provided |
| `items.*.name`                 | string  | The name for the order item                                                                       | No                                                                       |
| `items.*.url`                  | string  | The url for the order item                                                                        | No                                                                       |
| `items.*.sku`                  | string  | The sku for the order item, can be used to resolve buyable                                        | No                                                                       |
| `items.*.reference`            | string  | The **unique** reference for the order item                                                       | No                                                                       |
| `items.*.manufacturer_id`      | int     | The manufacturer id for the order item                                                            | No                                                                       |
| `items.*.image`                | string  | The image for the order item                                                                      | No                                                                       |
| `items.*.options`              | array   | The options for the order item                                                                    | No                                                                       |
| `items.*.shippable`            | boolean | Whether the order item is shippable                                                               | No                                                                       |
| `items.*.quantity`             | int     | The quantity for the order item                                                                   | Yes                                                                      |
| `items.*.price.amount`         | float   | The **unit** price of the order item **excluding tax**                                            | Yes                                                                      |
| `items.*.price.tax`            | float   | The **unit** tax for the order item                                                               | Yes                                                                      |
| `items.*.discount.amount`      | float   | The **total** discount of the order item **excluding tax**                                        | No                                                                       |
| `items.*.discount.tax`         | float   | The **total** discount tax for the order item                                                     | No                                                                       |
| `items.*.full_price.amount`    | float   | The **unit** full price (including extras) of the order item **excluding tax**                    | No                                                                       |
| `items.*.full_price.tax`       | float   | The **unit** full tax (including extras) for the order item                                       | No                                                                       |
| `items.*.cost_price.amount`    | float   | The **unit** cost price of the order item **excluding tax**                                       | No                                                                       |
| `items.*.cost_price.currency`  | string  | The currency code for the cost price                                                              | No                                                                       |
| `items.*.weight`               | float   | The weight for the order item                                                                     | No                                                                       |
| `items.*.weight_unit`          | float   | The weight unit for the order item, defaults to stores normalized <br/> weight unit if not passed | No                                                                       |
| `items.*.volume`               | float   | The volume for the order item                                                                     | No                                                                       |
| `items.*.volume_unit`          | float   | The volume unit for the order item, defaults to stores normalized <br/>volume unit if not passed  | No                                                                       |
| `items.*.tag_ids`              | array   | The tag ids for the order item                                                                    | No                                                                       |
| `items.*.hs`                   | string  | The HS code for the order item                                                                    | No                                                                       |
| `items.*.origin_country`       | string  | The origin country code for the order item                                                        | No                                                                       |
| `items.*.subscription_plan_id` | int     | The subscription plan id for the order item                                                       | No                                                                       |
| `items.*.goods_description`    | string  | The goods description for the order item                                                          | No                                                                       |

The buyable is used to initially populate the attributes of the order item and then any attributes passed are applied

`price`, `discount` & `full_price` all support an unnested price including tax being passed, see [Price Conventions](../../CONVENTIONS.md#price-conventions) for example

In the event an unnested price including tax is passed the ex and vat will be calculated using the buyables tax group

If no `full_price` is passed for the order item it is set to its `price`

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
