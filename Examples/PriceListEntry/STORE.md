# Store Price List Entry

## Overview

This endpoint creates a new price list entry using the provided json data

## Structure

### Price List Entry

| Name         | Type   | Description                                                                                                                                   | Required    |
|--------------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| `id`         | int    | The id for the entry                                                                                                                          | No          |
| `for`        | string | What the entry applies to (e.g., all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)                    | Yes         |
| `target`     | string | Identifier of the target (e.g., id corresponding to the `for` or model for product, or sku for variant or name for category/tag/manufacturer) | Conditional |
| `type`       | string | Type of the price adjustment (e.g., fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase)        | Yes         |
| `price`      | object | The [Price](#price) object (not required when `type` is *percentage* based)                                                                   | Conditional |
| `percentage` | float  | The percentage of the price list entry (only required when `type` is *percentage* based)                                                      | Conditional |
| `for_price`  | string | Which price the entry affects (e.g., sale_price, base_price, rrp, cost_price)                                                                 | Yes         |

### Price

| Name       | Type     | Description                                                           | Required |
|------------|----------|-----------------------------------------------------------------------|----------|
| `amount`   | float    | The price **including tax**, in whole units (e.g. pounds not pence)   | Yes      |
| `currency` | string   | The currency for the price, e.g. GBP                                  | Yes      |


## Example Request

```http request
POST /api/price-lists/{id}/entries
```

```json lines
{
    "for": "variant",
    "target": "sku",
    "type": "percentage_decrease",
    "percentage": 20,
    "for_price": "base_price"
}
```

[Back to contents](../../README.md#table-of-contents)
