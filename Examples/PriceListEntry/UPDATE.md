# Update Price List Entry

## Attributes:

### Price List Entry

| Name            | Type     | Description                                                                                                                                            | Required |
|-----------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| `for`           | string   | The for of the price list entry (all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)                             | No       |
| `target`        | string   | The target of the price list entry (e.g. id corresponding to the `for` or model for product, or sku for variant or name for category/tag/manufacturer) | No       |
| `type`          | string   | The type of the price list entry (fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase)                   | No       |
| `price`         | object   | The price of the price list entry, see [Price](#price) (NOTE: Don't use when `type` is percentage based)                                               | No       |
| `percentage`    | float    | The percentage of the price list entry (NOTE: Only use when `type` is percentage based)                                                                | No       |
| `for_price`     | string   | The price that the price list entry affects (sale_price, base_price, rrp, cost_price)                                                                  | No       |


### Price

| Name               | Type     | Description                                                           | Required |
|--------------------|----------|-----------------------------------------------------------------------|----------|
| `price.amount`     | float    | The price **including tax**, in whole units (e.g. pounds not pence)   | Yes      |
| `price.currency`   | string   | The currency for the price, e.g. GBP                                  | Yes      |


## Example Request

```http request
POST /api/price-lists/{priceListId}/entries/{priceListEntryId}
```

```json lines
{
    "for": "product",
    "target": 2,
    "type": "percentage_decrease",
    "percentage": 20
}
```
