# View Price List

## Overview

This endpoint retrieves a single price list by `id`

## Structure

### Price List

| Name                           | Type       | Description                                                                         |
|--------------------------------|------------|-------------------------------------------------------------------------------------|
| `id`                           | int        | The id of the price list                                                            |
| `name`                         | string     | The name of the price list                                                          |
| `applies_to`                   | string     | The applies to of the price list (e.g., everyone, not-customers, customers, groups) |
| `start_at`                     | timestamp  | The start at of the price list                                                      |
| `end_at`                       | timestamp  | The end at of the price list                                                        |
| `entries`                      | array      | An array of [Entry](#entry) objects                                                 |
| `customer_groups`              | array      | An array of [Customer Group](#customer-group) objects                               |

### Entry

| Name         | Type   | Description                                                                                                                        |
|--------------|--------|------------------------------------------------------------------------------------------------------------------------------------|
| `id`         | int    | The id of the price list entry                                                                                                     |
| `for`        | string | What the entry applies to (e.g., all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)         |
| `target`     | string | Identifier of the target (if applicable) — e.g. product id, variant id, category id, etc...                                        |
| `type`       | string | Type of price adjustment (e.g., fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase) |
| `price`      | object | The [Price](#price) object (only present when `type` is *fixed* based)                                                             |
| `percentage` | float  | Percentage value (only present when `type` is *percentage* based)                                                                  |
| `for_price`  | string | Which price the entry affects (e.g., sale_price, base_price, rrp, cost_price)                                                      |

### Price

| Name       | Type     | Description                                                      |
|------------|----------|------------------------------------------------------------------|
| `amount`   | float    | The price **including tax**, in whole units (e.g., `10` = `£10`) |
| `currency` | string   | The currency for the price (e.g., GBP)                           |

### Customer Groups

| Name         | Type      | Description                         |
|--------------|-----------|-------------------------------------|
| `id`         | int       | The id of the customer group        |
| `name`       | string    | The name of the customer group      |
| `start_at`   | timestamp | The start at for the customer group |
| `end_at`     | timestamp | The end at for the customer group   |

## Example Response

```http request
GET /api/price-lists/{id}
```

```json lines
{
  "id": 1,
  "name": "API Test",
  "applies_to": "everyone",
  "start_at": null,
  "end_at": null,
  "entries": [
    {
      "id": 1,
      "for": "all_products",
      "target": null,
      "type": "fixed_price",
      "price": {
        "amount": 10,
        "currency": "GBP"
      },
      "for_price": "base_price"
    },
    {
      "id": 2,
      "for": "all_products_unless_reduced",
      "target": null,
      "type": "fixed_price_decrease",
      "price": {
        "amount": 10,
        "currency": "GBP"
      },
      "for_price": "base_price"
    },
    {
      "id": 3,
      "for": "product",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "id": 4,
      "for": "variant",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "id": 5,
      "for": "category",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "id": 6,
      "for": "tag",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "id": 7,
      "for": "manufacturer",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    }
  ],
  "customer_groups": []
}
```

[Back to contents](../../README.md#table-of-contents)
