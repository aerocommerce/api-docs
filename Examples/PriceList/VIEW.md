# View Product

## Attributes:

### Price List

| Name                           | Type   | Description                                                                    |
|--------------------------------|--------|--------------------------------------------------------------------------------|
| `id`                           | int    | The id of the price list                                                       |
| `name`                         | string | The name of the price list                                                     |
| `applies_to`                   | string | The applies to of the price list (everyone, not-customers, customers, groups)  |
| `start_at`                     | date   | The start at of the price list                                                 |
| `end_at`                       | date   | The end at of the price list                                                   |
| `entries`                      | array  | The entries of the price list, see [Entries](#entries)                         |
| `customer_groups`              | array  | The customer groups of the price list, see [Customer Groups](#customer-groups) |

### Entries

| Name                   | Type   | Description                                                                                                                          |
|------------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------|
| `entries.*.id`         | int    | The id of the price list entry                                                                                                       |
| `entries.*.for`        | string | The for of the price list entry (all_products, all_products_unless_reduced, product, variant, category, tag, manufacturer)           |
| `entries.*.target`     | string | The target of the price list entry (e.g. id corresponding to the `for` if applicable)                                                |
| `entries.*.type`       | string | The type of the price list entry (fixed_price, fixed_price_decrease, fixed_price_increase, percentage_decrease, percentage_increase) |
| `entries.*.price`      | object | The price of the price list entry, see [Price](#price) (NOTE: Not in payload when `type` is percentage based)                        |
| `entries.*.percentage` | float  | The percentage of the price list entry (NOTE: Only in payload when `type` is percentage based)                                       |
| `entries.*.for_price`  | string | The price that the price list entry affects (sale_price, base_price, rrp, cost_price)                                                |

### Price

| Name              | Type     | Description                                                         |
|-------------------|----------|---------------------------------------------------------------------|
| `price.amount`    | float    | The price **including tax**, in whole units (e.g. pounds not pence) |
| `price.currency`  | string   | The currency for the price, e.g. GBP                                |

### Customer Groups

| Name                         | Type   | Description                         |
|------------------------------|--------|-------------------------------------|
| `customer_groups.*.id`       | int    | The id of the customer group        |
| `customer_groups.*.name`     | string | The name of the customer group      |
| `customer_groups.*.start_at` | date   | The start at for the customer group |
| `customer_groups.*.end_at`   | date   | The end at for the customer group   |

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
