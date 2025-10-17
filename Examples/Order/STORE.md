# Store Order

## Overview

This endpoint creates a new order using the provided json data

## Structure

### Order

| Name                 | Type      | Description                                                                                                                  | Required?                   |
|----------------------|-----------|------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| `id`                 | int       | The id for the order                                                                                                         | No                          |
| `reference`          | string    | The **unique** reference for the order                                                                                       | Yes                         |
| `status_id`          | int       | The status id of the order, can also be resolved from `state`                                                                | If `ordered_at` is not null |
| `state`              | string    | Alternative to passing `status_id`, resolves the first status with the specified state                                       | No                          |
| `customer_id`        | int       | The id of the customer that placed the order                                                                                 | No                          |
| `email`              | string    | The email of the customer that placed the order                                                                              | No                          |
| `subtotal.amount`    | float     | The subtotal of the order **excluding tax** (in pence not pounds)                                                            | No                          |
| `subtotal.tax`       | float     | The subtotal tax for the order (in pence not pounds)                                                                         | No                          |
| `shipping.amount`    | float     | The shipping of the order **excluding tax** (in pence not pounds)                                                            | No                          |
| `shipping.tax`       | float     | The shipping tax for the order (in pence not pounds)                                                                         | No                          |
| `discount.amount`    | float     | The discount of the order **excluding tax** (in pence not pounds)                                                            | No                          |
| `discount.tax`       | float     | The discount tax for the order (in pence not pounds)                                                                         | No                          |
| `surcharge.amount`   | float     | The surcharge of the order **excluding tax** (in pence not pounds)                                                           | No                          |
| `surcharge.tax`      | float     | The surcharge tax for the order (in pence not pounds)                                                                        | No                          |
| `shipping_method_id` | int       | The shipping method id of the order                                                                                          | No                          |
| `currency`           | string    | The currency of the order, (defaults to store default if not provided)                                                       | No                          |
| `exchange_rate`      | float     | The exchange rate of the order (derives from currency if not supplied)                                                       | No                          |
| `shipping_address`   | object    | The [Shipping Address](#shipping-address) for the order                                                                      | No                          |
| `billing_address `   | object    | The [Billing Address](#billing-address) for the order                                                                        | No                          |
| `ip`                 | string    | The ip of the order                                                                                                          | No                          |
| `channel`            | string    | The channel of the order                                                                                                     | No                          |
| `subscription_id`    | int       | The subscription id of the order                                                                                             | No                          |
| `notify`             | boolean   | Whether the order notifications are activated (defaults to `true`)                                                           | No                          |
| `buy_items`          | boolean   | Whether the order items stock should be mutated. If false then `OrderItemBought` event will not be emit (defaults to `true`) | No                          |
| `ordered_at`         | timestamp | When the order was ordered                                                                                                   | No                          |
| `deliver_on`         | timestamp | When the order should be delivered                                                                                           | No                          |
| `items`              | array     | An array of [Order Item](#order-item) objects                                                                                | Yes                         |
| `payments`           | array     | An array of [Payment](#payment) objects                                                                                      | No                          |
| `fulfillments`       | array     | An array of [Fulfillment](#fulfillment) objects                                                                              | No                          |
| `comments`           | array     | An array of [Comment](#comment) objects                                                                                      | No                          |

- If no `subtotal.amount` or `subtotal.tax` is passed their values will be set to the sum of the items `price.amount` * `quantity` & `price.tax` * `quantity` respectively

- If no `discount.amount` or `discount.tax` is passed their values will be set to the sum of the items `discount.amount` & `discount.tax` respectively

### Shipping Address

| Name          | Type    | Description                                       | Required? |
|---------------|---------|---------------------------------------------------|-----------|
| `first_name`  | string  | The first name for the shipping address           | Yes       |
| `last_name`   | string  | The last name for the shipping address            | Yes       |
| `company`     | string  | The company for the shipping address              | No        |
| `mobile`      | string  | The mobile number for the shipping address        | No        |
| `phone`       | string  | The phone number for the shipping address         | No        |
| `line_1`      | string  | The first line for the shipping address           | Yes       |
| `line_2`      | string  | The second line for the shipping address          | No        |
| `city`        | string  | The city for the shipping address                 | Yes       |
| `zone`        | string  | The zone code for the shipping address            | No        |
| `postcode`    | string  | The postcode for the shipping address             | Yes       |
| `country`     | string  | The country code for the shipping address         | No        |
| `reference`   | string  | The **unique** reference for the shipping address | No        |
| `eori_number` | string  | The EORI number for the shipping address          | No        |

### Billing Address

| Name          | Type    | Description                                      | Required? |
|---------------|---------|--------------------------------------------------|-----------|
| `first_name`  | string  | The first name for the billing address           | Yes       |
| `last_name`   | string  | The last name for the billing address            | Yes       |
| `company`     | string  | The company for the billing address              | No        |
| `mobile`      | string  | The mobile number for the billing address        | No        |
| `phone`       | string  | The phone number for the billing address         | No        |
| `line_1`      | string  | The first line for the billing address           | Yes       |
| `line_2`      | string  | The second line for the billing address          | No        |
| `city`        | string  | The city for the billing address                 | Yes       |
| `zone`        | string  | The zone code for the billing address            | No        |
| `postcode`    | string  | The postcode for the billing address             | Yes       |
| `country`     | string  | The country code for the billing address         | No        |
| `reference`   | string  | The **unique** reference for the billing address | No        |
| `eori_number` | string  | The EORI number for the billing address          | No        |

### Order Item

| Name                   | Type    | Description                                                                                          | Required?                                                                |
|------------------------|---------|------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|
| `key`                  | string  | The unique key for the order item                                                                    | No                                                                       |
| `variant_id`           | int     | The variant id of the buyable                                                                        | No                                                                       |
| `product_id`           | string  | The product id of the buyable (resolves first variant unless variant_id is provided)                 | No                                                                       |
| `buyable_type`         | string  | The buyable type of the order item                                                                   | Not required if any of:<br/>`sku`/`variant_id`/`product_id` are provided |
| `buyable_id`           | int     | The buyable id of the order item                                                                     | Not required if any of:<br/>`sku`/`variant_id`/`product_id` are provided |
| `name`                 | string  | The name for the order item                                                                          | Conditional `*`                                                                       |
| `url`                  | string  | The url for the order item                                                                           | No                                                                       |
| `sku`                  | string  | The sku for the order item, can be used to resolve buyable                                           | Conditional `*`                                                           |
| `reference`            | string  | The **unique** reference for the order item                                                          | No                                                                       |
| `manufacturer_id`      | int     | The manufacturer id for the order item                                                               | No                                                                       |
| `image`                | string  | The image for the order item                                                                         | No                                                                       |
| `options`              | array   | The options for the order item                                                                       | No                                                                       |
| `shippable`            | boolean | Whether the order item is shippable                                                                  | No                                                                       |
| `quantity`             | int     | The quantity for the order item                                                                      | Yes                                                                      |
| `price.amount`         | float   | The **unit** price of the order item **excluding tax** (in pence not pounds)                         | Yes                                                                      |
| `price.tax`            | float   | The **unit** tax for the order item (in pence not pounds)                                            | Yes                                                                      |
| `discount.amount`      | float   | The **total** discount of the order item **excluding tax** (in pence not pounds)                     | No                                                                       |
| `discount.tax`         | float   | The **total** discount tax for the order item (in pence not pounds)                                  | No                                                                       |
| `full_price.amount`    | float   | The **unit** full price (including extras) of the order item **excluding tax** (in pence not pounds) | No                                                                       |
| `full_price.tax`       | float   | The **unit** full tax (including extras) for the order item (in pence not pounds)                    | No                                                                       |
| `cost_price.amount`    | float   | The **unit** cost price of the order item **excluding tax** (in pence not pounds)                    | No                                                                       |
| `cost_price.currency`  | string  | The currency code for the cost price                                                                 | No                                                                       |
| `weight`               | float   | The weight for the order item                                                                        | No                                                                       |
| `weight_unit`          | float   | The weight unit for the order item, defaults to stores normalized <br/> weight unit if not passed    | No                                                                       |
| `volume`               | float   | The volume for the order item                                                                        | No                                                                       |
| `volume_unit`          | float   | The volume unit for the order item, defaults to stores normalized <br/>volume unit if not passed     | No                                                                       |
| `tag_ids`              | array   | The tag ids for the order item                                                                       | No                                                                       |
| `hs`                   | string  | The HS code for the order item                                                                       | No                                                                       |
| `origin_country`       | string  | The origin country code for the order item                                                           | No                                                                       |
| `subscription_plan_id` | int     | The subscription plan id for the order item                                                          | No                                                                       |
| `goods_description`    | string  | The goods description for the order item                                                             | No                                                                       |

`*` If no buyable can be resolved from given data then the `sku` is required - as is the `name`

- `price`, `discount` & `full_price` all support an un-nested price including tax being passed, see [Price Conventions](../../CONVENTIONS.md#price-conventions)

### Payment

| Name        | Type   | Description                                                                 | Required?                           |
|-------------|--------|-----------------------------------------------------------------------------|-------------------------------------|
| `method_id` | int    | The payment method id of the payment                                        | Not required if `driver` is passed  |
| `driver`    | string | Payment driver used to resolve `method_id`                                  | No                                  |
| `reference` | string | The reference for the payment, if not specified a uuid will be generated    | No                                  |
| `state`     | string | The state for the payment, if not specified the captured state will be used | No                                  |
| `amount`    | float  | The total amount for the payment                                            | Yes                                 |

**Valid states:** failed, pending, authorized, partially captured, captured, partially refunded, refunded, canceled, errored

### Fulfillment

| Name            | Type         | Description                                                                                                    | Required? |
|-----------------|--------------|----------------------------------------------------------------------------------------------------------------|-----------|
| `id`            | int          | The id for the fulfillment                                                                                     | No        |
| `reference`     | string       | The reference for the fulfillment                                                                              | No        |
| `state`         | string       | The state of the fulfillment (defaults to method's default if not passed)                                      | No        |
| `method`        | int\| string | The fulfillment method's id, name or driver (defaults to orders' default if not passed)                        | No        |
| `tracking_code` | string       | The tracking code for the fulfillment                                                                          | No        |
| `tracking_url`  | url          | The tracking url for the fulfillment                                                                           | No        |
| `weight`        | float        | The total weight of the fulfillment (calculated from items if not passed)                                      | No        |
| `weight_unit`   | string       | The weight unit (defaults to store's default if not provided)                                                  | No        |
| `volume`        | float        | The total volume of the fulfillment (calculated from items if not passed)                                      | No        |
| `volume_unit`   | string       | The volume unit (defaults to store's default if not provided)                                                  | No        |
| `delivery_note` | string       | The delivery note for the fulfillment                                                                          | No        |
| `notify`        | boolean      | Whether the fulfillment notifications are activated (defaults to `true`)                                       | No        |
| `dispatched_at` | timestamp    | The dispatched at of the fulfillment                                                                           | No        |
| `items`         | array        | An array of [Fullfillment Item](#fulfillment-item) objects (if not passed every fulfillable item is fulfilled) | No        |

**Valid fulfillment states:** `failed`, `pending`, `open`, `successful`, `canceled`, `errored`

### Fulfillment Item

| Name          | Type   | Description                                                            | Required?       |
|---------------|--------|------------------------------------------------------------------------|-----------------|
| `id`          | int    | The id of the order item to be fulfilled                               | Conditional `*` |
| `sku`         | string | The sku of the order item to be fulfilled                              | Conditional `*` |
| `quantity`    | int    | The quantity to be fulfilled (defaults to max possible)                | No              |
| `weight`      | float  | The weight of the item (uses order item's weight if not passed)        | No              |
| `weight_unit` | string | The weight unit (defaults to store's default if not provided)          | No              |
| `volume`      | float  | The volume of the fulfillment (uses order item's volume if not passed) | No              |
| `volume_unit` | string | The volume unit (defaults to store's default if not provided)          | No              |

### Comment

| Name              | Type        | Description                                               | Required? |
|-------------------|-------------|-----------------------------------------------------------|-----------|
| `id`              | int         | The id for the comment                                    | No        |
| `admin`           | int\|string | The id or email of the admin                              | No        |
| `message`         | string      | The comment message                                       | Yes       |
| `customer_facing` | boolean     | Whether the comment is customer facing (default: `false`) | No        |
| `created_at`      | timestamp   | The date the comment was created (defaults to now)        | No        |

**NOTE:** If no `admin` is supplied then the API Token's name will be displayed for the comment in the admin

## Example Request

```http request
POST /api/orders
```

```json lines
{
    "reference": "ABC123",
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
            "variant_id": 1,
            "shippable": true,
            "quantity": 2,
            "price": {
                "amount": 42083.33,
                "tax": 8416.67
            },
            "discount": {
                "amount": 8416.67,
                "tax": 1683.33
            }
        }
    ],
    "payments": [
        {
            "driver": "cash",
            "amount": 91000
        }
    ],
    "comments": [
        {
            "admin": "admin@example.com",
            "message": "This is an API message",
            "created_at": "2025-09-01 09:29:41",
            "customer_facing": true
        }
    ]
}
```

## Example Response

```json
{
    "order": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
