# View Order

## Attributes:

### Order

| Name               | Type   | Description                                                                                 |
|--------------------|--------|---------------------------------------------------------------------------------------------|
| `reference`        | string | The **unique** reference for the order                                                      |
| `status`           | object | The status of the order, see [Order Status](#order-status)                                  |
| `state`            | string | Alternative to passing `status_id`, resolves <br/>the first status with the specified state |
| `customer`         | object | The customer of the order, see [Customer](#customer)                                        |
| `email`            | string | The email of the customer that placed the order                                             |
| `subtotal.amount`  | float  | The subtotal of the order **excluding tax**                                                 |
| `subtotal.tax`     | float  | The subtotal tax for the order                                                              |
| `shipping.amount`  | float  | The shipping of the order **excluding tax**                                                 |
| `shipping.tax`     | float  | The shipping tax for the order                                                              |
| `discount.amount`  | float  | The discount of the order **excluding tax**                                                 |
| `discount.tax`     | float  | The discount tax for the order                                                              |
| `surcharge.amount` | float  | The surcharge of the order **excluding tax**                                                |
| `surcharge.tax`    | float  | The surcharge tax for the order                                                             |
| `currency`         | string | The currency code of the order                                                              |
| `shipping_method`  | object | The shipping method of the order, see <br/>[Shipping Method](#shipping-method)              |
| `shipping_address` | object | The shipping address of the order,<br/>see [Shipping Address](#shipping-address)            |
| `billing_address ` | object | The billing address of the order,<br/>see [Billing Address](#billing-address)               |
| `ordered_at`       | date   | When the order was ordered                                                                  |
| `deliver_on`       | date   | When the order should be delivered                                                          |
| `items`            | array  | The items of the order,<br/>see [Order Items](#order-items)                                 |
| `payments`         | array  | The payments for the order,<br/>see [Payments](#payments)                                   |
| `returns`          | array  | The returns for the order,<br/>see [Returns](#returns)                                      |

### Order Status

An order can have a status, if it doesn't then `status` will be `null`, see attributes below:

| Name           | Type   | Description                   |
|----------------|--------|-------------------------------|
| `status.id`    | int    | The id of the order status    |
| `status.name`  | string | The name of the order status  |
| `status.state` | string | The state of the order status |

The `state` is restricted to one of the following values:
- cancelled
- on_hold
- successful
- complete
- processing
- closed
- partially_dispatched
- dispatched
- partially_returned
- returned

### Customer

An order can have a customer, if it doesn't then `customer` will be `null`, see attributes below:

| Name             | Type   | Description               |
|------------------|--------|---------------------------|
| `customer.id`    | int    | The id of the customer    |
| `customer.name`  | string | The name of the customer  |
| `customer.email` | string | The email of the customer |

### Shipping Method

An order can have a shipping method, if it doesn't then `shipping_method` will be `null`, see attributes below:

| Name                   | Type   | Description                     |
|------------------------|--------|---------------------------------|
| `shipping_method.id`   | int    | The id of the shipping method   |
| `shipping_method.name` | string | The name of the shipping method |

### Shipping Address

An order can have a shipping address, if it doesn't then `shipping_address` will be `null`, see attributes below:

| Name                               | Type    | Description                                       |
|------------------------------------|---------|---------------------------------------------------|
| `shipping_address.first_name`      | string  | The first name for the shipping address           |
| `shipping_address.last_name`       | string  | The last name for the shipping address            |
| `shipping_address.company`         | string  | The company for the shipping address              |
| `shipping_address.mobile`          | string  | The mobile number for the shipping address        |
| `shipping_address.phone`           | string  | The phone number for the shipping address         |
| `shipping_address.line_1`          | string  | The first line for the shipping address           |
| `shipping_address.line_2`          | string  | The second line for the shipping address          |
| `shipping_address.city`            | string  | The city for the shipping address                 |
| `shipping_address.zone`            | string  | The zone code for the shipping address            |
| `shipping_address.postcode`        | string  | The postcode for the shipping address             |
| `shipping_address.country`         | string  | The country code for the shipping address         |
| `shipping_address.reference`       | string  | The **unique** reference for the shipping address |
| `shipping_address.eori_number`     | string  | The EORI number for the shipping address          |

### Billing Address

An order can have a billing address, if it doesn't then `billing_address` will be `null`, see attributes below:

| Name                            | Type    | Description                                      |
|---------------------------------|---------|--------------------------------------------------|
| `billing_address.first_name`    | string  | The first name for the billing address           |
| `billing_address.last_name`     | string  | The last name for the billing address            |
| `billing_address.company`       | string  | The company for the billing address              |
| `billing_address.mobile`        | string  | The mobile number for the billing address        |
| `billing_address.phone`         | string  | The phone number for the billing address         |
| `billing_address.line_1`        | string  | The first line for the billing address           |
| `billing_address.line_2`        | string  | The second line for the billing address          |
| `billing_address.city`          | string  | The city for the billing address                 |
| `billing_address.zone`          | string  | The zone code for the billing address            |
| `billing_address.postcode`      | string  | The postcode for the billing address             |
| `billing_address.country`       | string  | The country code for the billing address         |
| `billing_address.reference`     | string  | The **unique** reference for the billing address |
| `billing_address.eori_number`   | string  | The EORI number for the billing address          |

### Order Items

An order has items, see attributes below:

| Name                          | Type    | Description                                                                                       |
|-------------------------------|---------|---------------------------------------------------------------------------------------------------|
| `items.*.id`                  | int     | The id of the order item                                                                          |
| `items.*.variant_id`          | int     | The variant id of the buyable (not set if the buyable is not a variant)                           |
| `items.*.product_id`          | int     | The product id of the buyable                                                                     |
| `items.*.buyable_type`        | string  | The buyable type of the order item                                                                |
| `items.*.buyable_id`          | int     | The buyable id of the order item                                                                  |
| `items.*.name`                | string  | The name for the order item                                                                       |
| `items.*.url`                 | string  | The url for the order item                                                                        |
| `items.*.sku`                 | string  | The sku for the order item                                                                        |
| `items.*.reference`           | string  | The **unique** reference for the order item                                                       |
| `items.*.manufacturer`        | object  | The manufacturer for the order item, see [Manufacturer](#manufacturer)                            |
| `items.*.image.url`           | string  | The image url for the order item                                                                  |
| `items.*.shippable`           | boolean | Whether the order item is shippable                                                               |
| `items.*.quantity`            | int     | The quantity for the order item                                                                   |
| `items.*.returned_quantity`   | int     | The quantity returned for the order item                                                          |
| `items.*.price.amount`        | float   | The **unit** price of the order item **excluding tax**                                            |
| `items.*.price.tax`           | float   | The **unit** tax for the order item                                                               |
| `items.*.discount.amount`     | float   | The **total** discount of the order item **excluding tax**                                        |
| `items.*.discount.tax`        | float   | The **total** discount tax for the order item                                                     |
| `items.*.full_price.amount`   | float   | The **unit** full price (including extras) of the order item **excluding tax**                    |
| `items.*.full_price.tax`      | float   | The **unit** full tax (including extras) for the order item                                       |
| `items.*.cost_price.amount`   | float   | The **unit** cost price of the order item **excluding tax**                                       |
| `items.*.cost_price.currency` | string  | The currency code for the cost price                                                              |
| `items.*.weight`              | float   | The weight for the order item                                                                     |
| `items.*.weight_unit`         | float   | The weight unit for the order item, defaults to stores normalized <br/> weight unit if not passed |
| `items.*.volume`              | float   | The volume for the order item                                                                     |
| `items.*.volume_unit`         | float   | The volume unit for the order item, defaults to stores normalized <br/>volume unit if not passed  |
| `items.*.hs`                  | string  | The HS code for the order item                                                                    |
| `items.*.origin_country`      | string  | The origin country code for the order item                                                        |
| `items.*.goods_description`   | string  | The goods description for the order item                                                          |

### Manufacturer

An order item can have a manufacturer, if it doesn't then `manufacturer` will be `null`, see attributes below:

| Name                | Type   | Description                  |
|---------------------|--------|------------------------------|
| `manufacturer.id`   | string | The id of the manufacturer   |
| `manufacturer.name` | string | The name of the manufacturer |

### Payments

| Name                     | Type   | Description                                                       |
|--------------------------|--------|-------------------------------------------------------------------|
| `payments.*.id`          | string | The id of the payment                                             |
| `payments.*.method`      | object | The method for the payment, see [Payment Method](#payment-method) |
| `payments.*.reference`   | string | The reference for the payment                                     |
| `payments.*.state`       | string | The state of the payment                                          |
| `payments.*.amount`      | float  | The total amount for the payment                                  |
| `payments.*.currency`    | string | The currency code for the payment                                 |
| `payments.*.captured_at` | date   | The date the payment was captured                                 |

### Payment Method

| Name            | Type   | Description                      |
|-----------------|--------|----------------------------------|
| `method.id`     | int    | The id of the payment method     |
| `method.name`   | string | The name of the payment method   |
| `method.driver` | string | The driver of the payment method |

### Returns

| Name                   | Type   | Description                                                |
|------------------------|--------|------------------------------------------------------------|
| `returns.*.id`         | int    | The id of the order return                                 |
| `returns.*.reason`     | string | The reason for the return - `null` if no reason given      |
| `returns.*.created_at` | date   | The date the return was made                               |
| `returns.*.items`      | array  | The items of the return, see [Return Items](#return-items) |

### Return Items

| Name                       | Type | Description                                                                                    |
|----------------------------|------|------------------------------------------------------------------------------------------------|
| `items.*.id`               | int  | The id of the order item that was returned                                                     |
| `items.*.quantity`         | int  | The quantity of the order item that was returned                                               |
| `items.*.exchanged_for_id` | int  | The id of the order item that the item was returned for (`null` if the item was not exchanged) |

## Example Response

```http request
GET /api/orders/{id}
```

OR

```http request
GET /api/orders?id={id}
```

OR

```http request
GET /api/orders?reference={reference}
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
    "currency": "GBP",
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
            "amount": 101100,
            "currency": "GBP",
            "captured_at": "2023-09-12T10:17:03.000000Z"
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
