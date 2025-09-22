# View Shipping Method

## Overview

This endpoint retrieves a single shipping method by `id`

## Structure

### Shipping Method

| Name        | Type    | Description                                      |
|-------------|---------|--------------------------------------------------|
| `id`        | int     | The id of the shipping method                    |
| `name`      | string  | The name of the shipping method                  |
| `available` | boolean | Whether the shipping method is available for use |
| `rates`     | array   | An array of [Rate](#rate) objects                |

### Rate

| Name         | Type   | Description                                                                |
|--------------|--------|----------------------------------------------------------------------------|
| `id`         | int    | The id of the shipping rate                                                |
| `currency`   | string | ISO currency code of the shipping rate (e.g., GBP)                         |
| `min_price`  | float  | Minimum cart total price for this rate to apply                            |
| `max_price`  | float  | Maximum cart total price for this rate to apply (nullable = no limit)      |
| `min_weight` | float  | Minimum total weight for this rate to apply                                |
| `max_weight` | float  | Maximum total weight for this rate to apply (nullable = no limit)          |
| `min_volume` | float  | Minimum total volume for this rate to apply                                |
| `max_volume` | float  | Maximum total volume for this rate to apply (nullable = no limit)          |
| `price`      | float  | The cost of shipping, expressed in the specified currency’s smallest units |

## Example Response

```http request
GET /api/shipping-methods/{id}
```

```json lines
{
    "id": 2,
    "name": "Standard",
    "available": true,
    "rates": [
        {
            "id": 2,
            "currency": "GBP",
            "min_price": 1000,
            "max_price": null,
            "min_weight": 0,
            "max_weight": null,
            "min_volume": 0,
            "max_volume": null,
            "price": 12300
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
