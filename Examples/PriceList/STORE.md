# Store Price List

## Attributes:

### Price List

| Name                | Type     | Description                                                                                                       | Required |
|---------------------|----------|-------------------------------------------------------------------------------------------------------------------|----------|
| `name`              | string   | The name of the price list                                                                                        | Yes      |
| `applies_to`        | string   | The applies to of the price list (everyone, not-customers, customers, groups)                                     | Yes      |
| `start_at`          | date     | The start at of the price list                                                                                    | No       |
| `end_at`            | date     | The end at of the price list                                                                                      | No       |
| `entries`           | array    | The entries of the price list, see [Entries](#entries)                                                            | No       |
| `customer_groups`   | array    | The customer groups of the price list (only when `applies_to` is groups), see [Customer Groups](#customer-groups) | No       |


### Entries

| Name                    | Type     | Description                                                                                                                                            | Required     |
|-------------------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| `entries.*.for`         | string   | The for of the price list entry (all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)                             | Yes          |
| `entries.*.target`      | string   | The target of the price list entry (e.g. id corresponding to the `for` or model for product, or sku for variant or name for category/tag/manufacturer) | Conditional  |
| `entries.*.type`        | string   | The type of the price list entry (fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase)                   | Yes          |
| `entries.*.price`       | object   | The price of the price list entry, see [Price](#price) (NOTE: Not required when `type` is percentage based)                                            | Conditional  |
| `entries.*.percentage`  | float    | The percentage of the price list entry (NOTE: Only required when `type` is percentage based)                                                           | Conditional  |
| `entries.*.for_price`   | string   | The price that the price list entry affects (sale_price, base_price, rrp, cost_price)                                                                  | Yes          |


### Price

| Name               | Type     | Description                                                           | Required |
|--------------------|----------|-----------------------------------------------------------------------|----------|
| `price.amount`     | float    | The price **including tax**, in whole units (e.g. pounds not pence)   | Yes      |
| `price.currency`   | string   | The currency for the price, e.g. GBP                                  | Yes      |


### Customer Groups

| Name                         | Type   | Description                         | Required  |
|------------------------------|--------|-------------------------------------|-----------|
| `customer_groups.*.id`       | int    | The id of the customer group        | Yes       |
| `customer_groups.*.start_at` | date   | The start at for the customer group | No        |
| `customer_groups.*.end_at`   | date   | The end at for the customer group   | No        |

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
