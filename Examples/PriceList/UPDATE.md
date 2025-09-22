# Update Price List

## Overview

This endpoint updates an existing price list by its `id`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Price List

| Name                | Type      | Description                                                                               | Required |
|---------------------|-----------|-------------------------------------------------------------------------------------------|----------|
| `name`              | string    | The name of the price list                                                                | No       |
| `applies_to`        | string    | The applies to of the price list (e.g., everyone, not-customers, customers, groups)       | No       |
| `start_at`          | timestamp | The start at of the price list                                                            | No       |
| `end_at`            | timestamp | The end at of the price list                                                              | No       |
| `customer_groups`   | array     | An array of [Customer Group](#customer-group) objects (only when `applies_to` = "groups") | No       |

### Customer Group

| Name       | Type      | Description                         | Required  |
|------------|-----------|-------------------------------------|-----------|
| `id`       | int       | The id of the customer group        | Yes       |
| `start_at` | timestamp | The start at for the customer group | No        |
| `end_at`   | timestamp | The end at for the customer group   | No        |

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

[Back to contents](../../README.md#table-of-contents)
