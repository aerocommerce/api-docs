# View Payment Method

## Overview

This endpoint retrieves a single payment method by `id`

## Structure

### Payment Method

| Name        | Type    | Description                                     |
|-------------|---------|-------------------------------------------------|
| `id`        | int     | The id of the payment method                    |
| `name`      | string  | The name of the payment method                  |
| `driver`    | string  | The driver for the payment method               |
| `available` | boolean | Whether the payment method is available for use |

## Example Response

```http request
GET /api/payment-methods/{id}
```

```json lines
{
    "id": 1,
    "name": "Cash",
    "driver": "cash",
    "available": true
}
```

[Back to contents](../../README.md#table-of-contents)
