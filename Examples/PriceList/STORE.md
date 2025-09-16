# Store Price List

## Overview

This endpoint creates a new price list using the provided json data

## Structure

### Price List

| Name                | Type      | Description                                                                                         | Required |
|---------------------|-----------|-----------------------------------------------------------------------------------------------------|----------|
| `name`              | string    | The name of the price list                                                                          | Yes      |
| `applies_to`        | string    | The applies to of the price list (everyone, not-customers, customers, groups)                       | Yes      |
| `start_at`          | timestamp | The start at of the price list                                                                      | No       |
| `end_at`            | timestamp | The end at of the price list                                                                        | No       |
| `entries`           | array     | An array of [Entry](#entry) objects                                                                 | No       |
| `customer_groups`   | array     | An array of [Customer Group](#customer-group) objects (only required when `applies_to` = "groups")  | No       |

### Entry

| Name         | Type     | Description                                                                                                                                   | Required     |
|--------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| `for`        | string   | What the entry applies to (e.g., all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)                    | Yes          |
| `target`     | string   | Identifier of the target (e.g., id corresponding to the `for` or model for product, or sku for variant or name for category/tag/manufacturer) | Conditional  |
| `type`       | string   | Type of the price adjustment (e.g., fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase)        | Yes          |
| `price`      | object   | The [Price](#price) object (not required when `type` is *percentage* based)                                                                   | Conditional  |
| `percentage` | float    | The percentage of the price list entry (only required when `type` is *percentage* based)                                                      | Conditional  |
| `for_price`  | string   | Which price the entry affects (e.g., sale_price, base_price, rrp, cost_price)                                                                 | Yes          |

### Price

| Name       | Type     | Description                                                      | Required |
|------------|----------|------------------------------------------------------------------|----------|
| `amount`   | float    | The price **including tax**, in whole units (e.g., `10` = `£10`) | Yes      |
| `currency` | string   | The currency for the price (e.g., GBP)                           | Yes      |


### Customer Group

| Name       | Type      | Description                         | Required  |
|------------|-----------|-------------------------------------|-----------|
| `id`       | int       | The id of the customer group        | Yes       |
| `start_at` | timestamp | The start at for the customer group | No        |
| `end_at`   | timestamp | The end at for the customer group   | No        |

## Example Request

```http request
POST /api/price-lists
```

```json lines
{
  "id": 1,
  "name": "API Test",
  "applies_to": "everyone",
  "entries": [
    {
      "for": "all_products",
      "type": "fixed_price",
      "price": {
        "amount": 10,
        "currency": "GBP"
      },
      "for_price": "base_price"
    },
    {
      "for": "all_products_unless_reduced",
      "type": "fixed_price_decrease",
      "price": {
        "amount": 10,
        "currency": "GBP"
      },
      "for_price": "base_price"
    },
    {
      "for": "product",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "for": "variant",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "for": "category",
      "target": 1,
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
      "for": "tag",
      "target": 1, 
      "type": "percentage_decrease",
      "percentage": 10,
      "for_price": "sale_price"
    },
    {
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
