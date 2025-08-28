# Update Price List

## Attributes:

### Price List

| Name                | Type     | Description                                                                                                       | Required |
|---------------------|----------|-------------------------------------------------------------------------------------------------------------------|----------|
| `name`              | string   | The name of the price list                                                                                        | No       |
| `applies_to`        | string   | The applies to of the price list (everyone, not-customers, customers, groups)                                     | No       |
| `start_at`          | date     | The start at of the price list                                                                                    | No       |
| `end_at`            | date     | The end at of the price list                                                                                      | No       |
| `customer_groups`   | array    | The customer groups of the price list (only when `applies_to` is groups), see [Customer Groups](#customer-groups) | No       |

### Customer Groups

| Name                         | Type   | Description                         | Required  |
|------------------------------|--------|-------------------------------------|-----------|
| `customer_groups.*.id`       | int    | The id of the customer group        | Yes       |
| `customer_groups.*.start_at` | date   | The start at for the customer group | No        |
| `customer_groups.*.end_at`   | date   | The end at for the customer group   | No        |

## Example Request

```http request
PUT /api/price-lists/{id}
```

```json lines
{
    "name": "API Test Updated",
    "applies_to": "customers"
}
```
