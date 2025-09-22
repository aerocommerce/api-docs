# View Order

## Overview

This endpoint retrieves a single order by `id` or `reference`

## Structure

### Order

| Name               | Type      | Description                                                           |
|--------------------|-----------|-----------------------------------------------------------------------|
| `reference`        | string    | The **unique** reference for the order                                |
| `status`           | object    | The [Order Status](#order-status) of the order (null if none)         |
| `customer`         | object    | The [Customer](#customer) of the order (null if none)                 |
| `email`            | string    | The email of the customer that placed the order                       |
| `subtotal.amount`  | float     | The subtotal of the order **excluding tax**                           |
| `subtotal.tax`     | float     | The subtotal tax for the order                                        |
| `shipping.amount`  | float     | The shipping of the order **excluding tax**                           |
| `shipping.tax`     | float     | The shipping tax for the order                                        |
| `discount.amount`  | float     | The discount of the order **excluding tax**                           |
| `discount.tax`     | float     | The discount tax for the order                                        |
| `surcharge.amount` | float     | The surcharge of the order **excluding tax**                          |
| `surcharge.tax`    | float     | The surcharge tax for the order                                       |
| `currency`         | string    | The currency code of the order                                        |
| `shipping_method`  | object    | The [Shipping Method](#shipping-method) of the order (null if none)   |
| `shipping_address` | object    | The [Shipping Address](#shipping-address) of the order (null if none) |
| `billing_address ` | object    | The [Billing Address](#billing-address) of the order (null if none)   |
| `ordered_at`       | timestamp | When the order was ordered                                            |
| `deliver_on`       | timestamp | When the order should be delivered                                    |
| `items`            | array     | An array of [Order Item](#order-item) objects                         |
| `payments`         | array     | An array of [Payment](#payment) objects                               |
| `fulfillments`     | array     | An array of [Fulfillment](#fulfillment) objects                       |
| `returns`          | array     | An array of [Return](#return) objects                                 |

### Order Status

| Name    | Type   | Description                   |
|---------|--------|-------------------------------|
| `id`    | int    | The id of the order status    |
| `name`  | string | The name of the order status  |
| `state` | string | The state of the order status |

**Valid states:** cancelled, on_hold, successful, complete, processing, closed, partially_dispatched, dispatched, partially_returned, returned

### Customer

| Name    | Type   | Description               |
|---------|--------|---------------------------|
| `id`    | int    | The id of the customer    |
| `name`  | string | The name of the customer  |
| `email` | string | The email of the customer |

### Shipping Method

| Name    | Type   | Description                     |
|---------|--------|---------------------------------|
| `id`    | int    | The id of the shipping method   |
| `name`  | string | The name of the shipping method |

### Shipping Address

| Name               | Type    | Description                                       |
|--------------------|---------|---------------------------------------------------|
| `first_name`       | string  | The first name for the shipping address           |
| `last_name`        | string  | The last name for the shipping address            |
| `company`          | string  | The company for the shipping address              |
| `mobile`           | string  | The mobile number for the shipping address        |
| `phone`            | string  | The phone number for the shipping address         |
| `line_1`           | string  | The first line for the shipping address           |
| `line_2`           | string  | The second line for the shipping address          |
| `city`             | string  | The city for the shipping address                 |
| `zone`             | string  | The zone code for the shipping address            |
| `postcode`         | string  | The postcode for the shipping address             |
| `country`          | string  | The country code for the shipping address         |
| `reference`        | string  | The **unique** reference for the shipping address |
| `eori_number`      | string  | The EORI number for the shipping address          |

### Billing Address

| Name             | Type    | Description                                      |
|------------------|---------|--------------------------------------------------|
| `first_name`     | string  | The first name for the billing address           |
| `last_name`      | string  | The last name for the billing address            |
| `company`        | string  | The company for the billing address              |
| `mobile`         | string  | The mobile number for the billing address        |
| `phone`          | string  | The phone number for the billing address         |
| `line_1`         | string  | The first line for the billing address           |
| `line_2`         | string  | The second line for the billing address          |
| `city`           | string  | The city for the billing address                 |
| `zone`           | string  | The zone code for the billing address            |
| `postcode`       | string  | The postcode for the billing address             |
| `country`        | string  | The country code for the billing address         |
| `reference`      | string  | The **unique** reference for the billing address |
| `eori_number`    | string  | The EORI number for the billing address          |

### Order Item

| Name                   | Type    | Description                                                                         |
|------------------------|---------|-------------------------------------------------------------------------------------|
| `id`                   | int     | The id of the order item                                                            |
| `variant_id`           | int     | The variant id of the buyable (not set if the buyable is not a variant)             |
| `product_id`           | int     | The product id of the buyable                                                       |
| `buyable_type`         | string  | The buyable type of the order item                                                  |
| `buyable_id`           | int     | The buyable id of the order item                                                    |
| `name`                 | string  | The name for the order item                                                         |
| `url`                  | string  | The url for the order item                                                          |
| `sku`                  | string  | The sku for the order item                                                          |
| `reference`            | string  | The **unique** reference for the order item                                         |
| `manufacturer`         | object  | The [Manufacturer](#manufacturer) for the order item (null if none)                 |
| `image.url`            | string  | The image url for the order item                                                    |
| `shippable`            | boolean | Whether the order item is shippable                                                 |
| `quantity`             | int     | The quantity for the order item                                                     |
| `returned_quantity`    | int     | The quantity returned for the order item                                            |
| `price.amount`         | float   | The **unit** price of the order item **excluding tax**                              |
| `price.tax`            | float   | The **unit** tax for the order item                                                 |
| `discount.amount`      | float   | The **total** discount of the order item **excluding tax**                          |
| `discount.tax`         | float   | The **total** discount tax for the order item                                       |
| `full_price.amount`    | float   | The **unit** full price (including extras) of the order item **excluding tax**      |
| `full_price.tax`       | float   | The **unit** full tax (including extras) for the order item                         |
| `cost_price.amount`    | float   | The **unit** cost price of the order item **excluding tax**                         |
| `cost_price.currency`  | string  | The currency code for the cost price                                                |
| `weight`               | float   | The weight for the order item                                                       |
| `weight_unit`          | float   | The weight unit for the order item, defaults to stores normalized <br/> weight unit |
| `volume`               | float   | The volume for the order item                                                       |
| `volume_unit`          | float   | The volume unit for the order item, defaults to stores normalized <br/>volume unit  |
| `hs`                   | string  | The HS code for the order item                                                      |
| `origin_country`       | string  | The origin country code for the order item                                          |
| `goods_description`    | string  | The goods description for the order item                                            |

### Manufacturer

| Name   | Type   | Description                  |
|--------|--------|------------------------------|
| `id`   | int    | The id of the manufacturer   |
| `name` | string | The name of the manufacturer |

### Payment

| Name           | Type      | Description                                           |
|----------------|-----------|-------------------------------------------------------|
| `id`           | int       | The id of the payment                                 |
| `method`       | object    | The [Payment Method](#payment-method) for the payment |
| `reference`    | string    | The reference for the payment                         |
| `state`        | string    | The state of the payment                              |
| `amount`       | float     | The total amount for the payment                      |
| `currency`     | string    | The currency code for the payment                     |
| `captured_at`  | timestamp | The date the payment was captured                     |

### Payment Method

| Name      | Type   | Description                      |
|-----------|--------|----------------------------------|
| `id`      | int    | The id of the payment method     |
| `name`    | string | The name of the payment method   |
| `driver`  | string | The driver of the payment method |

### Fulfillment

| Name            | Type      | Description                                                                          |
|-----------------|-----------|--------------------------------------------------------------------------------------|
| `id`            | int       | The id of the order return                                                           |
| `method`        | object    | The [Fulfillment Method](#fulfillment-method) for the fulfillment                    |
| `reference`     | string    | The reference of the fulfillment                                                     |
| `state`         | string    | The state of the fulfillment                                                         |
| `mobile`        | string    | The mobile number for the fulfillment                                                |
| `phone`         | string    | The phone number for the fulfillment                                                 |
| `tracking_code` | string    | The tracking code for the fulfillment                                                |
| `tracking_url`  | string    | The tracking url for the fulfillment                                                 |
| `weight`        | float     | The weight for the fulfillment                                                       |
| `weight_unit`   | string    | The weight unit for the fulfillment, defaults to stores normalized <br/> weight unit |
| `volume`        | float     | The volume for the order item                                                        |
| `volume_unit`   | string    | The volume unit for the fulfillment, defaults to stores normalized <br/>volume unit  |
| `delivery_note` | string    | The delivery note for the fulfillment                                                |
| `created_at`    | timestamp | The date the fulfillment was made                                                    |
| `items`         | array     | An array of [Fulfillment Items](#fulfillment-items) objects                          |

### Fulfillment Method

| Name       | Type   | Description                          |
|------------|--------|--------------------------------------|
| `id`       | int    | The id of the fulfillment method     |
| `name`     | string | The name of the fulfillment method   |
| `driver`   | string | The driver of the fulfillment method |

### Fulfillment Items

| Name       | Type | Description                                                                                    |
|------------|------|------------------------------------------------------------------------------------------------|
| `id`       | int  | The id of the order item that was fulfilled                                                    |
| `quantity` | int  | The quantity of the order item that was fulfilled                                              |

### Returns

| Name           | Type      | Description                                           |
|----------------|-----------|-------------------------------------------------------|
| `id`           | int       | The id of the order return                            |
| `reason`       | string    | The reason for the return - `null` if no reason given |
| `created_at`   | timestamp | The date the return was made                          |
| `items`        | array     | An array of [Return Item](#return-item) objects       |

### Return Item

| Name                | Type | Description                                                                                    |
|---------------------|------|------------------------------------------------------------------------------------------------|
| `id`                | int  | The id of the order item that was returned                                                     |
| `quantity`          | int  | The quantity of the order item that was returned                                               |
| `exchanged_for_id`  | int  | The id of the order item that the item was returned for (`null` if the item was not exchanged) |

## Example Request

### 1. Unfulfilled & Unreturned Order Response

```http request
GET /api/orders/{id|reference}
```

```json
{
    "id": 1,
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
    "surcharge": {
        "amount": 0,
        "tax": 0
    },
    "ordered_at": "2023-09-01T09:29:41.000000Z",
    "deliver_on": null,
    "currency": "GBP",
    "status": {
        "id": 3,
        "name": "Successful",
        "state": "successful"
    },
    "customer": {
        "id": 1,
        "name": "Test",
        "email": "test@gmail.com"
    },
    "shipping_method": {
        "id": 1,
        "name": "Standard"
    },
    "billing_address": {
        "id": 1,
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
        "id": 1,
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
    ],
    "payments": [
        {
            "id": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "method": {
                "id": 1,
                "name": "Cash",
                "driver": "cash"
            },
            "reference": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "amount": 91000,
            "currency": "GBP",
            "captured_at": "2023-09-12T10:17:03.000000Z"
        }
    ],
    "fulfillments": [],
    "returns": []
}
```

### 2. Fulfilled Order Response

```http request
GET /api/orders/{id|reference}
```

```json
{
    "id": 1,
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
    "surcharge": {
        "amount": 0,
        "tax": 0
    },
    "currency": "GBP",
    "ordered_at": "2023-09-01T08:29:41.000000Z",
    "deliver_on": null,
    "status": {
        "id": 6,
        "name": "Dispatched",
        "state": "dispatched"
    },
    "customer": {
        "id": 1,
        "name": "Test",
        "email": "test@gmail.com"
    },
    "shipping_method": {
        "id": 1,
        "name": "Standard"
    },
    "billing_address": {
        "id": 1,
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
        "country": "GB",
        "eori_number": null
    },
    "shipping_address": {
        "id": 1,
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
        "country": "GB",
        "eori_number": null
    },
    "items": [
        {
            "id": 26,
            "name": "Sandro Paris Checked Trench Coat",
            "url": "/product/sandro-paris-checked-trench-coat-4?variant=2",
            "sku": "SHPMA00148-M",
            "reference": null,
            "manufacturer": {
                "id": 2,
                "name": "Sandro Paris"
            },
            "image": {
                "url": "http://l9.test/storage/images/products/uaaVbTbqbZxs1FH3N28Tw0a7dc6I7Xd08DiyPAG6.jpg"
            },
            "product_id": 4,
            "variant_id": 14,
            "buyable_type": "variant",
            "buyable_id": 14,
            "shippable": true,
            "quantity": 2,
            "returned_quantity": 0,
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
            "volume": 0,
            "cost_price": {
                "amount": null,
                "currency": null
            },
            "hs": null,
            "origin_country": null,
            "goods_description": null
        }
    ],
    "flags": [],
    "payments": [
        {
            "id": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "method": {
                "id": 1,
                "name": "Cash",
                "driver": "cash"
            },
            "reference": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "state": "captured",
            "amount": 91000,
            "currency": "GBP",
            "captured_at": "2023-09-12T10:17:03.000000ZZ",
            "refunds": []
        }
    ],
    "fulfillments": [
        {
            "id": 3,
            "method": {
                "id": 1,
                "name": "Manual Fulfillment",
                "driver": "manual"
            },
            "address": {
                "id": 3,
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
                "country": "GB",
                "eori_number": null
            },
            "reference": "F3-128",
            "state": "successful",
            "mobile": null,
            "email": "testing@gmail.com",
            "tracking_code": "test tracking code",
            "tracking_url": null,
            "weight": 0,
            "weight_unit": null,
            "volume": 0,
            "volume_unit": "cm^3",
            "delivery_note": "test delivery note",
            "created_at": "2023-09-12T10:17:03.000000Z",
            "items": [
                {
                    "id": 26,
                    "quantity": 2
                }
            ]
        }
    ],
    "returns": []
}
```

### 3. Returned Order Response (Exchange)

```http request
GET /api/orders/{id|reference}
```

```json
{
    "id": 1,
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
    "surcharge": {
        "amount": 0,
        "tax": 0
    },
    "currency": "GBP",
    "ordered_at": "2023-09-01T08:29:41.000000Z",
    "deliver_on": null,
    "status": {
        "id": 7,
        "name": "Partially Returned",
        "state": "partially_returned"
    },
    "customer": {
        "id": 1,
        "name": "Test",
        "email": "test@gmail.com"
    },
    "shipping_method": {
        "id": 1,
        "name": "Standard"
    },
    "billing_address": {
        "id": 1,
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
        "country": "GB",
        "eori_number": null
    },
    "shipping_address": {
        "id": 1,
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
        "country": "GB",
        "eori_number": null
    },
    "items": [
        {
            "id": 26,
            "name": "Sandro Paris Checked Trench Coat",
            "url": "/product/sandro-paris-checked-trench-coat-4?variant=2",
            "sku": "SHPMA00148-M",
            "reference": null,
            "manufacturer": {
                "id": 2,
                "name": "Sandro Paris"
            },
            "image": {
                "url": "http://l9.test/storage/images/products/uaaVbTbqbZxs1FH3N28Tw0a7dc6I7Xd08DiyPAG6.jpg"
            },
            "product_id": 4,
            "variant_id": 14,
            "buyable_type": "variant",
            "buyable_id": 14,
            "shippable": true,
            "quantity": 2,
            "returned_quantity": 0,
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
            "volume": 0,
            "cost_price": {
                "amount": null,
                "currency": null
            },
            "hs": null,
            "origin_country": null,
            "goods_description": null
        }
    ],
    "flags": [],
    "payments": [
        {
            "id": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "method": {
                "id": 1,
                "name": "Cash",
                "driver": "cash"
            },
            "reference": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "state": "captured",
            "amount": 91000,
            "currency": "GBP",
            "captured_at": "2023-09-12T10:17:03.000000ZZ",
            "refunds": []
        }
    ],
    "fulfillments": [],
    "returns": [
        {
            "id": 1,
            "reason": "Test Reason",
            "created_at": "2023-09-12T10:17:03.000000ZZ",
            "items": [
                {
                    "id": 26,
                    "quantity": 2,
                    "exchanged_for_id": 27
                }
            ]
        }
    ]
}
```

### 4. Returned Order Response (Refund)

```http request
GET /api/orders/{id|reference}
```

```json
{
    "id": 1,
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
    "surcharge": {
        "amount": 0,
        "tax": 0
    },
    "currency": "GBP",
    "ordered_at": "2023-09-01T08:29:41.000000Z",
    "deliver_on": null,
    "status": {
        "id": 8,
        "name": "Returned",
        "state": "returned"
    },
    "customer": {
        "id": 1,
        "name": "Test",
        "email": "test@gmail.com"
    },
    "shipping_method": {
        "id": 1,
        "name": "Standard"
    },
    "billing_address": {
        "id": 1,
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
        "country": "GB",
        "eori_number": null
    },
    "shipping_address": {
        "id": 1,
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
        "country": "GB",
        "eori_number": null
    },
    "items": [
        {
            "id": 26,
            "name": "Sandro Paris Checked Trench Coat",
            "url": "/product/sandro-paris-checked-trench-coat-4?variant=2",
            "sku": "SHPMA00148-M",
            "reference": null,
            "manufacturer": {
                "id": 2,
                "name": "Sandro Paris"
            },
            "image": {
                "url": "http://l9.test/storage/images/products/uaaVbTbqbZxs1FH3N28Tw0a7dc6I7Xd08DiyPAG6.jpg"
            },
            "product_id": 4,
            "variant_id": 14,
            "buyable_type": "variant",
            "buyable_id": 14,
            "shippable": true,
            "quantity": 2,
            "returned_quantity": 0,
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
            "volume": 0,
            "cost_price": {
                "amount": null,
                "currency": null
            },
            "hs": null,
            "origin_country": null,
            "goods_description": null
        }
    ],
    "flags": [],
    "payments": [
        {
            "id": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "method": {
                "id": 1,
                "name": "Cash",
                "driver": "cash"
            },
            "reference": "a53c31f9-43bd-4fc4-b308-cded0b533a2c",
            "state": "captured",
            "amount": 91000,
            "currency": "GBP",
            "captured_at": "2023-09-12T10:17:03.000000ZZ",
            "refunds": [
                {
                    "id": 1,
                    "amount": 91000,
                    "created_at": "2025-09-16T07:40:22.000000Z"
                }
            ]
        }
    ],
    "fulfillments": [],
    "returns": [
        {
            "id": 1,
            "reason": "Test reason",
            "created_at": "2025-09-16T07:40:22.000000Z",
            "items": [
                {
                    "id": 28,
                    "quantity": 2,
                    "exchanged_for_id": null
                }
            ]
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
