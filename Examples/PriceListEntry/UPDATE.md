# Update Price List Entry

## Overview

This endpoint updates an existing price list entry by its `id`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Price List Entry

| Name         | Type     | Description                                                                                                                                   | Required |
|--------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------|----------|
| `for`        | string   | What the entry applies to (e.g., all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)                    | No       |
| `target`     | string   | Identifier of the target (e.g., id corresponding to the `for` or model for product, or sku for variant or name for category/tag/manufacturer) | No       |
| `type`       | string   | Type of the price adjustment (e.g., fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase)        | No       |
| `price`      | object   | The [Price](#price) object (not when `type` is *percentage* based)                                                                            | No       |
| `percentage` | float    | The percentage of the price list entry (only when `type` is *percentage* based)                                                               | No       |
| `for_price`  | string   | Which price the entry affects (e.g., sale_price, base_price, rrp, cost_price)                                                                 | Yes      |

### Price

| Name         | Type     | Description                                                           | Required |
|--------------|----------|-----------------------------------------------------------------------|----------|
| `amount`     | float    | The price **including tax**, in whole units (e.g. pounds not pence)   | Yes      |
| `currency`   | string   | The currency for the price, e.g. GBP                                  | Yes      |

## Example Request

```http request
POST /api/price-lists/{priceListId}/entries/{priceListEntryId}
```

```json lines
{
    "for": "product",
    "target": "model",
    "type": "percentage_decrease",
    "percentage": 20
}
```

[Back to contents](../../README.md#table-of-contents)
